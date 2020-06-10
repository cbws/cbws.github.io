The projects service defines the following permissions and roles.

## Permissions

### Project

| Action            | Description                                                                          |
| ----------------- | ------------------------------------------------------------------------------------ |
| get               | Getting information about a project.                                                 |                   
| getIAMPolicy      | Getting IAM policy of a project.                                                     |                   
| setIAMPolicy      | Setting IAM policy of a project. This will also allow the principal to give themselves more rights on the project, so be careful in giving this permission. |                                                    |                   

## Roles

All roles that have been defined by the projects service.

### Organization

| Role            | Description                          |
| --------------- | ------------------------------------ |
| Project creator | Gives ability to create new projects |

### Project

| Role            | Description                                                                          |
| --------------- | ------------------------------------------------------------------------------------ |
| Project owner   | Gives full access to all resources within a project and the project itself, this is automatically assigned during project creation. |                   
| Project viewer  | Gives read-only access to most resources within a project.                           |
