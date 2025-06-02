As described in our [[authorization model documentation|Development authentication and authorization#Authorization]],
we use a combination of role- and activity-based authorization. Every
action in the system is controlled by an "activity" permission. Roles are
essentially a collection of activities.

### Roles

The system has some predefined roles. New roles can be added as the system
is running, and the predefined roles can be modified. These are the roles
as they are defined at the "beginning":

| Name               | Activities                                                                                                                                                 | Description                                                                                                                                                                                                    |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| eAPD Federal Admin    | view-roles<br>view-state-admins<br>edit-state-admins<br>view-affiliations<br>edit-affiliations<br>view-state-certifications<br>edit-state-certifications       | CMS APD federal administrators in charge of approving state administrators
| eAPD State Admin  | view-roles<br>view-affiliations<br>edit-affiliations<br>create-draft<br>view-document<br>edit-document<br>export-document                                                | Needs to be able to draft, submit, and respond to a "state specific" submission.<br><br>Should not have access to other states, unless access is granted.<br><br>Responsible for approving role requests from users within their state.                                                      |
| eAPD State Staff          | create-draft<br>view-document<br>edit-document<br>export-document                                                                                                            | Needs to be able to draft, submit, and respond to a "state specific" submission.<br><br>Should not have access to other states, unless access is granted. |
| eAPD State Contractor          | create-draft<br>view-document<br>edit-document<br>export-document                                                                                                            | Needs to be able to draft, submit, and respond to a "state specific" submission.<br><br>Should not have access to other states, unless access is granted. |


### Activities

The list of activities is fixed and is based on the things the system knows
how to do. Here are those activities:

| Name                    | Description                                                                    |
| ----------------------- | ------------------------------------------------------------------------------ |
| view-users              | Allows the user to view the list of all users or a specific user in the system |
| view-roles              | Allows the user to view the list of all roles in the system                    |
| export-document         | Allows the user to export an APD document                                      |
| create-draft            | Allows the user to create a draft APD                                          | 
| edit-document           | Allows the user to edit a non-submitted document                               |
| view-document           | Allows the user to view an APD document                                        |
| view-affiliations       | Allows the user to view affiliations for their state                           |
| edit-affiliations       | Allows the user to edit affiliations for their state                           |
| view-state-admins       | Allows the user to view state administrators                                   |
| edit-state-admins       | Allows the user to edit state administrators                                   |
| view-state-certifications       | Allows the user to download/view a state certification file                               |
| edit-state-certifications       | Allows the user to upload/add a state certification file                     |
