# WorkItem Updater

## Overview
The WorkItem Updater task can update workitems using a Query or that are linked to the Build/Release.  
The following workitem fields can be updated:
- Update the state for workitems.  
- Update the assignee for workitems.  
- Update the swimlane or board-column for workitems.  
- Add the build as Development Link to the workitems.
  
By adding this task to specific milestones in a build/release pipeline, you can create an automated kanban board.  
An example would be to set the state to 'Resolved' as the last step of a build and to 'Deployed' as the last step of a release.  
With this task the state of workitems is always reflecting reality and developers don't need to manually update workitems anymore.  
  
A preview of what the task can do, can be seen in this recording:  
  
![AutoKanban](marketplace/AutoKanban.gif)  
  
## Settings
| Name                           | Label                                                   | Description                                                                                                                                                                                                                                                                                                                                                                                                          | Options                                                                                                                                                     | Visible                                                       |
|--------------------------------|---------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| workitemsSource                | WorkItem source                                         | The source of the workitems to update.                                                                                                                                                                                                                                                                                                                                                                               | <ul><li>WorkItems linked to the Build/Release</li><li>a WorkItem Query</li></ul>                                                                            |                                                               |
| workitemsSourceQuery           | Query                                                   | The query to use as the workitem source.                                                                                                                                                                                                                                                                                                                                                                             |                                                                                                                                                             | workitemsSource == Query                                      |
| workItemType                   | WorkItem Type                                           | The type of workitems to update, e.g. User Story, Task or Bug. You can use a comma-separated string to supply multiple values.                                                                                                                                                                                                                                                                                       |                                                                                                                                                             |                                                               |
| workitemLimit                  | WorkItem Limit                                          | The number of workitems to update                                                                                                                                                                                                                                                                                                                                                                                    |                                                                                                                                                             |                                                               |
| allWorkItemsSinceLastRelease   | Include workitems since previously completed deployment | While deploying a release to an environment, update all workitems since the previously completed deployment.                                                                                                                                                                                                                                                                                                         |                                                                                                                                                             |                                                               |
| workItemState                  | WorkItem State                                          | The state to update the workitems to                                                                                                                                                                                                                                                                                                                                                                                 |                                                                                                                                                             |                                                               |
| workItemCurrentState           | Filter by WorkItem Current State                        | If defined, only update workitems that currently have this state. Leave empty to update from any state. Separate different valid states with ','                                                                                                                                                                                                                                                                     |                                                                                                                                                             |                                                               |
| workItemKanbanLane             | Board Swimlane                                          | If defined, the board Swimlane to update the workitems to.                                                                                                                                                                                                                                                                                                                                                           |                                                                                                                                                             |                                                               |
| workItemKanbanState            | Board column                                            | If defined, the board column to update the workitems to.                                                                                                                                                                                                                                                                                                                                                             |                                                                                                                                                             |                                                               |
| workItemDone                   | Move to board column Done                               | Move the workitem to the board column 'Done' for split board columns.                                                                                                                                                                                                                                                                                                                                                |                                                                                                                                                             |                                                               |
| linkBuild                      | Add Build as Development link                           | Add the build as a Development link to the WorkItem.                                                                                                                                                                                                                                                                                                                                                                 |                                                                                                                                                             |                                                               |
| updateAssignedTo               | Update 'Assigned To'                                    | Update the 'Assigned To' field of the workitem.                                                                                                                                                                                                                                                                                                                                                                      | <ul><li>Never</li><li>Only if unassigned</li><li>Always</li></ul>                                                                                           |                                                               |
| updateAssignedToWith           | Update 'Assigned To' with                               | Update the 'Assigned To' field of the workitem with a specific user.                                                                                                                                                                                                                                                                                                                                                 | <ul><li>Requester of the build</li><li>Creator of the workitem</li><li>User who started the item</li><li>Fixed user</li><li>Unassign the workitem</li></ul> | updateAssignedTo != Never                                     |
| assignedTo                     | Assign to                                               | The user to assign the workitem to.                                                                                                                                                                                                                                                                                                                                                                                  |                                                                                                                                                             | updateAssignedTo != Never && updateAssignedToWith = FixedUser |
| bypassRules                    | Bypass rules                                            | Bypass the rules that have been configured for the workitem type.                                                                                                                                                                                                                                                                                                                                                    |                                                                                                                                                             |                                                               |
| failTaskIfNoWorkItemsAvailable | Fail the task when there are no workitems               | If there are no workitems found to update, the task will fail.                                                                                                                                                                                                                                                                                                                                                       |                                                                                                                                                             |                                                               |
| comment                        | Comments to add                                         | A comment to add to every work item that is updated                                                                                                                                                                                                                                                                                                                                                                  |                                                                                                                                                             |                                                               |
| updateFields                   | Fields to update                                        | List of fields and values to update. Place each field on a new line and separate the fieldname and value with a comma.<br/>Fieldnames can be found using: [Work Item Types Field - List](https://docs.microsoft.com/en-us/rest/api/azure/devops/wit/work%20item%20types%20field/list?view=azure-devops-rest-5.0)<br/>As an example:<br/><br/>System.Description,This is a test description<br/>Custom.TestField,True |                                                                                                                                                             |                                                               |
| addTags                        | Tags to add                                             | Tags to assign to the workitem. Enter a tag per line.                                                                                                                                                                                                                                                                                                                                                                |                                                                                                                                                             |                                                               |
| removeTags                     | Tags to remove                                          | Tags to remove from the workitem. Enter a tag per line.                                                                                                                                                                                                                                                                                                                                                              |                                                                                                                                                             |                                                               |

