# Nodebb Admin panel settings

Before attaching discussion forum with context, we need to update some settings in nodebb admin panel. You can follow this document to update the admin settings.

### **Prerequisite** <a href="#prerequisite" id="prerequisite"></a>

1. Redis should be up and running.
2. Local nodebb should be up and running.

### Admin Settings

**Step:1**

Go to nodebb folder and run your local nodebb. Using below commands.

```
./nodebb start
./nodebb build
```

**Step:2**

Open this url in browser [http://loclahost:4567](http://localhost:4567/) and login as admin.

**Step:3**

You see this page. click on gear icon to navigate to nodebb admin panel.

![](<../../../../.gitbook/assets/image (7).png>)

**Step:4**

After that you will land on this page. Use settings tab to change the below option which is mention in table.

![](<../../../../.gitbook/assets/image (3) (1).png>)

|    | **Column name**                                                 | **Value**        | **Location**                                                                             |
| -- | --------------------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------- |
| 1  | Number of seconds between posts                                 | 0                | [/settings/post](https://preprod.ntp.net.in/discussions/admin/settings/post)             |
| 2  | Seconds between posts for new users                             | 5                | [/settings/post](https://preprod.ntp.net.in/discussions/admin/settings/post)             |
| 3  | Seconds before a new user can make their first post             | 0                | [/settings/post](https://preprod.ntp.net.in/discussions/admin/settings/post)             |
| 4  | Number of seconds a post remains editable (set to 0 to disable) | 0                | [/settings/post](https://preprod.ntp.net.in/discussions/admin/settings/post)             |
| 5  | Enable Traffic Management                                       | disable          | [/settings/advanced](https://preprod.ntp.net.in/discussions/admin/settings/advanced)     |
| 6  | Topics per Page                                                 | 50               | [/settings/pagination](https://preprod.ntp.net.in/discussions/admin/settings/pagination) |
| 7  | Maximum topics per page                                         | 50               | [/settings/pagination](https://preprod.ntp.net.in/discussions/admin/settings/pagination) |
| 8  | Default Topic Sorting                                           | Newest to Oldest | [/settings/post](https://preprod.ntp.net.in/discussions/admin/settings/post)             |
| 9  | Default Post Sorting                                            | Oldest to Newest | /[settings/post](https://preprod.ntp.net.in/discussions/admin/settings/post)             |
| 10 | Downvotes per day (set to 0 for unlimited downvotes)            | 0                | [/settings/reputation](https://preprod.ntp.net.in/discussions/admin/settings/reputation) |
| 11 | Downvotes per user per day (set to 0 for unlimited downvotes)   | 0                | [/settings/reputation](https://preprod.ntp.net.in/discussions/admin/settings/reputation) |
| 12 | Minimum reputation to downvote posts                            | -5               | [/settings/reputation](https://preprod.ntp.net.in/discussions/admin/settings/reputation) |
| 13 | Posts per Page                                                  | 50               | [/settings/pagination](https://preprod.ntp.net.in/discussions/admin/settings/pagination) |
| 14 | Maximum posts per page                                          | 50               | [/settings/pagination](https://preprod.ntp.net.in/discussions/admin/settings/pagination) |
| 15 | Pagination Settings                                             | Enable           | [/settings/pagination](https://preprod.ntp.net.in/discussions/admin/settings/pagination) |

***
