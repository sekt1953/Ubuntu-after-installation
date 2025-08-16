# Sharing data on Ubuntu 24.04

For sharing data on Ubuntu 24.04, a good approach is to create a dedicated directory, like /srv/shared, and set up appropriate permissions for users and groups.
This keeps shared data separate from individual user home directories and allows for controlled access.
Here's a more detailed breakdown:

## 1. Choose a Location:

### Recommended location: /srv/shared/

This is a common and recommended location for site-specific data that needs to be shared. The Filesystem Hierarchy Standard (FHS) suggests /srv for this purpose.

### Alternatives

You could also create a directory under **/var** or even a separate mount point if you have specific needs.

## 2. Create the Directory and Set Permissions

* Create the directory:
  * Use the command sudo mkdir /srv/shared (or your chosen location). 
* Create a shared group:
  * Create a new group (e.g., "shared-users") using sudo groupadd shared-users. 
* Add users to the group:
  * Add users who need access to the shared data using
    * sudo usermod -a -G shared-users [username].
* Change ownership and permissions:
  * Set the directory's group ownership and permissions:
    * sudo chown :shared-users /srv/shared
  * The 2770 permission sets the setgid bit, which ensures new files and directories created within the shared directory also inherit the "shared-users" group.
    * sudo chmod 2770 /srv/shared.

### Copy Code

```code
sudo mkdir /srv/shared
```

```code
sudo groupadd shared-users
```

```code
sudo usermod -a -G shared-users [username]
```

```code
sudo chown :shared-users /srv/shared
```

```code
sudo chmod 2770 /srv/shared
```

## 3. Accessing the Shared Data

* From the same machine: 
  * Users in the "shared-users" group can access the directory directly
* From other machines: 
  * You can use Samba for sharing with Windows machines, or NFS for other Linux systems.
* Why this approach is good:
  * Organization: Separates shared data from personal user files.
  * Security: Allows controlled access through group permissions.
  * Standard compliance: Uses a recommended location for shared data.
  * Flexibility: Can be easily adapted for different sharing needs.