ldhr
====

Linux Directory Hierarchy Replicator

GOAL

The goal of this project is to create system that replicates a directory structure between two Linux nodes securely, reliably and with minimal overhead.

LDHR:
- will use inotify to detect directory structure changes
- will use SQLITE to store 
- will initially call 'rsync' to copy files between the systems, later this should use librsync or similar
- will use a queuing system to every events occur on the target system in the same order as the source system

CHALLENGES

An inotify 'watch' can only monitor a single directory, so multiple inotify watches need to be set, one for echo sub-directory under the specified 'root'.  This is significant as it looks like we need a thread or process for every sub-directory and on a typical fileserver, this can easily reach 10s or 100s of thousands of sub-directories, which would overwealm the system.



