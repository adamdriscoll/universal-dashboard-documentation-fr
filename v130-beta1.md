# [v1.3.0-beta1](https://www.powershellgallery.com/packages/UniversalDashboard/1.3.0-beta1)

**Released: 12-11-2017**

### Issues Resolved

For more information, see below.

* Inputs for charts
* Endpoint debugging
* Endpoint initialization script

#### Inputs for charts \([\#181](https://github.com/adamdriscoll/poshprotools/issues/181)\)

Charts and monitors can now define filter fields to change the data show in the chart. You can use New-UDInputField and the FilterFields parameter of both New-UDChart and New-UDMonitor to define the input fields you would like to show. Next, just like New-UDInput, you can define parameters in the param block to accept the variables defined by the input fields.

```powershell
            New-UDChart -Title "Chart" -Id "Chart" -Type Line -EndPoint {
                param($Text, $Select) 

                $data = @(
                    [PSCustomObject]@{"Day" = 1; Jpg = "10"; MP4= "30"}
                    [PSCustomObject]@{"Day" = 2; Jpg = "20"; MP4= "20"}
                    [PSCustomObject]@{"Day" = 3; Jpg = "30"; MP4= "10"}
                )

                if ($Text -eq "Test") {
                    $data += [PSCustomObject]@{"Day" = 4; Jpg = "40"; MP4= "0"}
                }

                if ($Select -eq "Test2") {
                    $data += [PSCustomObject]@{"Day" = 5; Jpg = "50"; MP4= "100"}
                }

                $data | Out-UDChartData -LabelProperty "Day" -Dataset @(
                    New-UDChartDataset -DataProperty "Jpg" -Label "Jpg" -BackgroundColor "#80962F23" -HoverBackgroundColor "#80962F23"
                    New-UDChartDataset -DataProperty "MP4" -Label "MP4" -BackgroundColor "#8014558C" -HoverBackgroundColor "#8014558C"
                ) 
            } -FilterFields {
                New-UDInputField -Type "textbox" -Name "Text" -Placeholder 'Test Stuff'
                New-UDInputField -Type "select" -Name "Select" -Placeholder 'Test Other Stuff' -Values @("Test", "Test2", "Test3")
            }
```

Here's an example of the above chart. ![](/assets/capture-1.gif)

### Endpoint Debugging

Universal Dashboard creates a pool of runspaces to execute Endpoint script blocks. Even with the ability to debug runspaces in a process with Debug-Runspace, it's very difficult to identify the runspace that will end up running your endpoint because UD chooses which ever runspace is available. With v1.3.0-beta1, you can now use the -DebugEndpoint flag on components like charts, monitors and grids to ensure that the endpoint is run in the new "UDDebug" runspace.

This runspace is created only if the -DebugEndpoint is used and your Endpoint script block is being called. You can use Debug-Runspace to attach to the runspace and step through the code, inspect variables and identify errors.

Assume I have a dynamic column that calls the Endpoint script block below.

```powershell
            New-UDRow -Columns {
                New-UDColumn -Size 12 -Endpoint {
                    $MyVariable = Get-Random
                    $MyVariable2 = Get-Random

                    New-UDCard -Title $MyVariable -Text $MyVariable2
                } -DebugEndpoint
            }
```

I can now use Get-Runspace and Debug-Runspace to attach to the UDDebug runspace.

```powershell
PS C:\Users\adamr> Get-Runspace

 Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
  2 UDDebug         localhost       Local         Opened        Available

PS C:\Users\adamr> Debug-Runspace -Name UDDebug
```

### Endpoint Initialization Script

New-UDDashboard and Start-UDRestApi now expose a EndpointInitializationScript parameter. This parameter is used to provide a script block that will be run when initializing any runspace that executes an Endpoint script block. You can import modules, define variables and even functions.

```powershell
        $dashboard = New-UDDashboard -Title "Test" -Content {
            New-UDRow -Columns {
                New-UDColumn -Size 12 -Endpoint {
                    New-UDCard -Title $TitleVariable -Text (Get-ContentForCard) -Id "Card" 
                }
                New-UDColumn -Size 12 -Endpoint {
                    New-UDCard -Title $TitleVariable -Text (Get-ContentForCard) -Id "Card2" 
                }
                New-UDColumn -Size 12 -Endpoint {
                    New-UDCard -Title $TitleVariable -Text (Get-ContentForCard) -Id "Card3" 
                }
            }
        } -EndpointInitializationScript {
            $TitleVariable = "Title"
            function Get-ContentForCard {
                "Body"
            }
        }
```

## 



