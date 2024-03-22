---
title: "copy-or-sync"
output: html_document
date: "2024-03-22"
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## Copy vs Sync

**Copy** 
Copy files from source to dest, skipping identical files.

Copy the source to the destination. Does not transfer files that are identical on source and destination, testing by size and modification time or MD5SUM. Doesn't delete files from the destination. If you want to also delete files from destination, to make it match source, use the sync command instead. 

#####  syntax: rclone copy source:sourcepath dest:destpath 

Note that it is always the contents of the directory that is synced, not the directory itself. So when source:path is a directory, it's the contents of source:path that are copied, not the directory name and contents.

To copy single files, use the copyto command instead.

If dest:path doesn't exist, it is created and the source:path contents go there.


**Sync** 
Make source and dest identical, modifying destination only.

Sync the source to the destination, changing the destination only. Doesn't transfer files that are identical on source and destination, testing by size and modification time or MD5SUM. Destination is updated to match source, including deleting files if necessary (except duplicate objects, see below). If you don't want to delete files from destination, use the copy command instead.

##### syntax: rclone sync --interactive SOURCE remote:DESTINATION
