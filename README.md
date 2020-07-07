# Server Administration Quick Reference

## Table of Contents
- [Introduction](#introduction)
- [Filesystem Commands](#filesystem-commands)
    + [Zeroing out a file](#zeroing-out-a-file)
    + [Grep multiple files across multiple directories](#grep-multiple-files-across-multiple-directories)
    + [Find files larger than 1000000 bytes](#find-files-larger-than-1000000-bytes)
    + [Find files modified 3 or fewer days ago](#find-files-modified-3-or-fewer-days-ago)
    + [Delete object files and print what's deleted](#delete-object-files-and-print-what-s-deleted)
    + [Show list of directories and their sizes in kilobytes](#show-list-of-directories-and-their-sizes-in-kilobytes)
    + [Show how much space a directory is taking up in kilobytes](#show-how-much-space-a-directory-is-taking-up-in-kilobytes)
    + [Determine what process has a file open](#determine-what-process-has-a-file-open)
    + [Monitor a directory for open filehandles. Repeat command every second forever.](#monitor-a-directory-for-open-filehandles-repeat-command-every-second-forever)
    + [Show space on drives](#show-space-on-drives)
    + [Querying file locks max value on HP-UX](#querying-file-locks-max-value-on-hp-ux)
    + [Create a file of a given size](#create-a-file-of-a-given-size)
    + [Delete file by inode](#delete-file-by-inode)
    + [Search/Replace in a file](#search-replace-in-a-file)
    + [Delete logfiles without an open file handle](#delete-logfiles-without-an-open-file-handle)
    + [Determine if it is an HDD or SSD (0 means SSD, 1 means HDD)](#determine-if-it-is-an-hdd-or-ssd--0-means-ssd--1-means-hdd-)
    + [Manually formatting and mounting a block device](#manually-formatting-and-mounting-a-block-device)
- [Kubernetes Commands](#kubernetes-commands)
  * [General Commands](#general-commands)
    + [Login on Azure](#login-on-azure)
    + [Get Context](#get-context)
    + [Pods](#pods)
    + [Services](#services)
    + [Deployments](#deployments)
    + [Configmaps](#configmaps)
    + [SSH](#ssh)
    + [Endpoints](#endpoints)
    + [Secrets](#secrets)
    + [Ingress](#ingress)
    + [Events](#events)
    + [Logs](#logs)
    + [Horizontal Pod Autoscaler](#horizontal-pod-autoscaler)
    + [Scale Deployment](#scale-deployment)
  * [Setting up Ingress](#setting-up-ingress)
    + [Create Cert](#create-cert)
    + [Add Cert](#add-cert)
    + [Create Public IP on Azure](#create-public-ip-on-azure)
    + [Create Ingress Controller](#create-ingress-controller)
    + [Deploy App](#deploy-app)
  * [Log Analytics on Azure](#log-analytics-on-azure)
    + [CPU Graph](#cpu-graph)
    + [Events](#events-1)
- [Vim](#vim)
    + [Removing ^M characters at end of lines in vi](#removing--m-characters-at-end-of-lines-in-vi)
    + [Comment a block of text in vim](#comment-a-block-of-text-in-vim)
    + [Copy column in vim](#copy-column-in-vim)
    + [Opening a new file in vim](#opening-a-new-file-in-vim)
    + [List buffers](#list-buffers)
    + [Switch to a different buffer](#switch-to-a-different-buffer)
    + [Open file in new tab](#open-file-in-new-tab)
    + [Multiple Windows in Vim](#multiple-windows-in-vim)
    + [Enable mouse in vim (lets you resize split windows)](#enable-mouse-in-vim--lets-you-resize-split-windows-)
    + [Set tab to 4 spaces](#set-tab-to-4-spaces)
    + [Enable tab character](#enable-tab-character)
- [Miscellaneous](#miscellaneous)
    + [Sending a text file via e-mail](#sending-a-text-file-via-e-mail)
    + [Show how many rows and columns your display is set to](#show-how-many-rows-and-columns-your-display-is-set-to)
    + [System logs are located at:](#system-logs-are-located-at-)
    + [List all files in tar archive](#list-all-files-in-tar-archive)
    + [Tar a directory](#tar-a-directory)
    + [See which packages are assigned where in a failover](#see-which-packages-are-assigned-where-in-a-failover)
      - [HP-UX](#hp-ux)
      - [AIX](#aix)
    + [Getting a list of installed packages on hp](#getting-a-list-of-installed-packages-on-hp)
    + [Getting list of products from a depot file (HP-UX)](#getting-list-of-products-from-a-depot-file--hp-ux-)
    + [Installing product from a depot (HP-UX)](#installing-product-from-a-depot--hp-ux-)
    + [Getting a list of installed packages an AIX](#getting-a-list-of-installed-packages-an-aix)
    + [Converting unix epoch seconds to exec serial date format](#converting-unix-epoch-seconds-to-exec-serial-date-format)
    + [Print contents of a file in reverse order](#print-contents-of-a-file-in-reverse-order)
    + [Get checksum of a file](#get-checksum-of-a-file)
    + [Search contents of all files in a directory for a string](#search-contents-of-all-files-in-a-directory-for-a-string)
    + [Repeat a command every 5 seconds](#repeat-a-command-every-5-seconds)
    + [Show OS limits for a process (Linux only)](#show-os-limits-for-a-process--linux-only-)
    + [Print file in binary format](#print-file-in-binary-format)
    + [Print file in hexadecimal format](#print-file-in-hexadecimal-format)
    + [Print file in octal format](#print-file-in-octal-format)
    + [See all environment variables for a process running on Linux:](#see-all-environment-variables-for-a-process-running-on-linux-)
    + [Getting Centrify info on a user](#getting-centrify-info-on-a-user)
    + [Check if a server is a physical or virtual](#check-if-a-server-is-a-physical-or-virtual)
      - [Linux](#linux)
      - [AIX](#aix-1)
      - [HP-UX](#hp-ux-1)
      - [Windows](#windows)
    + [List kernel parameters](#list-kernel-parameters)
      - [HP-UX 11.11](#hp-ux-1111)
      - [HP-UX 11.23 and above](#hp-ux-1123-and-above)
      - [Redhat](#redhat)
    + [SSH to box without password](#ssh-to-box-without-password)
    + [Getting process list with full arguments an HP-UX](#getting-process-list-with-full-arguments-an-hp-ux)
    + [Syncronize panes in Tmux](#syncronize-panes-in-tmux)
    + [Bind key for synchronize-panes in Tmux](#bind-key-for-synchronize-panes-in-tmux)
    + [Switching version of a tool on Redhat](#switching-version-of-a-tool-on-redhat)
    + [Color diff in two columns](#color-diff-in-two-columns)




## Introduction

This is an assorted list of potentially useful Unix commands. These are commands I've found useful in the past that I don't want to forget.


## Filesystem Commands

#### Zeroing out a file

    cat/dev/null > <filename>



#### Grep multiple files across multiple directories

    find . -type f -print | xargs fgrep -i -l "text_to_grep_for"


#### Find files larger than 1000000 bytes

    ll -R <directoryname> | awk '{if ($5 > 1000000) print $5 "\t" $9}'

    find . -xdev -size +1000000c

On Linux:

    find . -xdev -size +1000000c -exec ls -al {} \; | sort -k 5n

On HP-UX:

    find . -xdev -size +1000000c -exec ls -al {} \; | sort -r +4n


#### Find files modified 3 or fewer days ago

On Linux:

    find . -xdev -type f -mtime 3 -exec ls -al {} \; | sort -rk +5n

On HP-UX:

    find . -xdev -type f -mtime 3 -exec ls -al {} \; | sort -r +4n


#### Delete object files and print what's deleted

    find . -name "*.o" -exec echo 'rm -f {}' \; -exec rm -f {} \;


#### Show list of directories and their sizes in kilobytes

On Linux:

    du -xhk | sort -k 1n

On HP-UX:

    du -xk | sort +0n


#### Show how much space a directory is taking up in kilobytes

    du -xks


Alternate version (only shows one level):

    du -shx



#### Determine what process has a file open

    fuser -u /path/to/file

    psg <pid>



#### Monitor a directory for open filehandles. Repeat command every second forever.

    while true; do lsof +d /tmp; sleep 1; done



#### Show space on drives

    df -k


#### Querying file locks max value on HP-UX

    kcusage | grep nflocks


#### Create a file of a given size

    dd if=/dev/zero of=don.out bs=1024 count=10240



#### Delete file by inode

    ls -li

    find . inem <inode number> -exec rm -l {} \;



#### Search/Replace in a file

    sed -ri 's/(test1|test2)/value3/g' app.cfg



#### Delete logfiles without an open file handle

    find /tmp -type f -exec bash -c "fuser {} || rm {}" \;



#### Determine if it is an HDD or SSD (0 means SSD, 1 means HDD)

    cat /sys/block/sdc/queue/rotational  



#### Manually formatting and mounting a block device

    lsblk  
    file -s /dev/xvdb  
    mkfs -t ext4 /dev/xvdb  
    mkdir /mnt/jenkins  
    mount /dev/xvdb /mnt/jenkins  
    ll /mnt/jenkins  
    df -h  


## Kubernetes Commands

### General Commands

#### Login on Azure

    az aks get-credentials --name <resource name> -g <resource group>

    az aks get-credentials --name <resource name> -g <resource group> --admin



#### Get Context

    kubectl config -get-contexts



#### Pods

    kubectl get pods --all-namespaces

    kubectl get pods -l app=nginx-ingress --all-namespaces

    kubectl get pods -l app=nginx-ingress -o wide --namespace=kube-system

    kubectl describe pods <pod name> --namespace=kube-system



#### Services

    kubectl get services --all-namespaces

    kubectl get svc <service name> --namespace=kube-system

    kubectl describe services --all-namespaces

    kubectl describe svc <service name> --namespace=kube-system



#### Deployments

    kubectl describe deployment <deployment name>



#### Configmaps

    kubectl get configmaps

    kubectl get configmaps --namespace=kube-system

    kubectl get configmaps --namespace=kube-system -o yaml



#### SSH

    kubectl exec -it <pod name> -- /bin/bash

    kubectl exec -it <pod name>-n <namespace> -- /bin/bash



#### Endpoints

    kubectl get ep



#### Secrets

    kubectl get secrets --all-namespaces



#### Ingress

    kubectl get ingress



#### Events

    kubectl get events --all-namespaces



#### Logs

    kubectl logs <pod name> --namespace <namespace name>

    kubectl logs -f <pod name>



#### Horizontal Pod Autoscaler

    kubectl autoscale deployment <deployment name> --cpu-percent=50 --min=1 --max=10

    kubectl get hpa

    kubectl describe hpa



#### Scale Deployment

    kubectl scale --replicas =3 <deployment name> -n <namespace name>



### Setting up Ingress

#### Create Cert

    openssl req -new -newkey rsa:4096 -x509 -sha256 -days 365 -nodes -out don_test.crt -keyout don_test.key


#### Add Cert

    kubectl create secret tls <secret name> --cert=don_test.crt --key=don_test.key



#### Create Public IP on Azure

    az network public-ip create -g <resource group name> -n <namespace name> --alocation-method static --reverse-fqdn example.westus.cloudapp.azure.com --dns-name example



#### Create Ingress Controller

    helm install <chart name> --namespace <namspace name> --set controller.service.loadBalancerIP="<insert ip here>" --set controller.replicaCount=2



#### Deploy App

    kubectl apply -f <yaml filename>





### Log Analytics on Azure

#### CPU Graph

    Perf |where CounterName == "cpuUsageNaneCores and ObjectName == "K8SContainer"

    | where TimeGenerated > ago(1d)

    | summarize avg(CounterValue), percentiles(CounterValue, 50, 95) by bin(TimeGenerated, 1h)



#### Events

    KubeEvents | where TimeGenerated > ago(1d)

    KubeEvents | where SourceComponent == "cluster-autoscaler"



## Vim

#### Removing ^M characters at end of lines in vi

    :%s/^V^M//g

The ^V is a CONTROL-V character and ^M is a CONTROL-M. When you type this, it will look like this:

    :%s/^M//g

alternate command:

    dos2unix <filename>


#### Comment a block of text in vim

- control-V
- \<highlight text with cursor\> (use arrow keys. Only one column will be highlighted)
- shift-I
- \#
- escape


#### Copy column in vim

 - control-V
 - \<highlight text with cursor\>
 - p



#### Opening a new file in vim

    :n <filename>

    :e <filename>



#### List buffers

    :ls



#### Switch to a different buffer

    :b<buffer number>

    :bnext

    :bprev



#### Open file in new tab

    :tabe <filename>



#### Multiple Windows in Vim

| Syntax | Description |
| ----------- | ----------- |
| :split \<filename\> | split window and load another file |
| vplit \<filename\> | vertical split |
| ctrl-w up arrow | move cursor up a window |
| ctrl-w ctrl-w | move cursor to another window (cycle) |
| ctrl-w_ | maxmize current window |
| ctrl-w= | make all equal size |
| 10 ctrl-w+ | increase window size by 10 lines |
| :hide | close current window |
| :only | keep only this window open |


#### Enable mouse in vim (lets you resize split windows)
    :set mouse=a


#### Set tab to 4 spaces

    set smartindent
    set tabstob=4
    set shiftwidth=4
    set expandtab


#### Enable tab character
    set noexpandtab


## Miscellaneous

#### Sending a text file via e-mail

    mailx -s "SUBJECT" email@example.com < file.out


#### Show how many rows and columns your display is set to

    resize



#### System logs are located at:

On Linux:

    /var/log/messages

On HP-UX:

    /var/adm/syslog


#### List all files in tar archive

    tar -tvf filename.tar



#### Tar a directory

    tar -cvf <name>.tar <directoryname>



#### See which packages are assigned where in a failover

##### HP-UX

    cmviewcl

##### AIX

      /usr/sbin/cluster/utilities/clfindres

Or this command:

      /usr/sbin/cluster/clstat



#### Getting a list of installed packages on hp

    swlist

    swlist -l patch



#### Getting list of products from a depot file (HP-UX)

    swlist -d -s <depot filename>



#### Installing product from a depot (HP-UX)

    swinstall -s <depot filename>



#### Getting a list of installed packages an AIX

    lslpp -L



#### Converting unix epoch seconds to exec serial date format

    =A1/86400+(25569-(5/24))



#### Print contents of a file in reverse order

    sed -s '1!G;h;$p'



#### Get checksum of a file

    cksum <filename>



#### Search contents of all files in a directory for a string

    grep "string to search" *



#### Repeat a command every 5 seconds

    watch -n5 <command>



#### Show OS limits for a process (Linux only)

    cat /proc/<PID>/llimits



#### Print file in binary format

xxd -b <filename>



#### Print file in hexadecimal format

    hexdump <filename>



#### Print file in octal format

    od <filename>



#### See all environment variables for a process running on Linux:

    xargs -n 1 0 < /proc/<PID>/environ



#### Getting Centrify info on a user

    adinfo -u <user id>



#### Check if a server is a physical or virtual

##### Linux

    dmidecode -t 1

Output:

    "Manufacturer: Vmware, Inc." is a virtual



##### AIX

    lparstat -I | grep Type

Output:

    Shared-SMT is a virtual

    Dedicated-SMT is physical


##### HP-UX

    model

Output:

    "ia64 hp server Integrity Virtual Machine" is a virtual

    "ia64 hp server rx260" is a physical



##### Windows

    systeminfo


Output:

    "System Manufacturer: System Manufacturer" is a physical

    "System Manufacturer: Vmware, Inc. System Model: VMWare Virtual Platform" is a virtual



#### List kernel parameters

##### HP-UX 11.11

    /usr/sbin/kmtune -l



##### HP-UX 11.23 and above

    kctune

    cat /stand/tunes


List details about a particular parameter

    kctune -v -q maxuprc



##### Redhat

    sysctl -a





#### SSH to box without password

    ssh-keygen -t rsa

    ssh-copy-id <userid>@<hostname>

    ssh <userid>@<hostname>


#### Getting process list with full arguments an HP-UX

    /usr/bin/env UNIX95=1 /bin/ps -eo 'state,uid,ppid,args'



#### Syncronize panes in Tmux

    :setw synchronize-panes


#### Bind key for synchronize-panes in Tmux

    bind a set-window-option synchronize-panes



#### Switching version of a tool on Redhat

    scl enable python27 python (opens a python shell)

    scl enable python27 bash (opens a new bash shell with python configured)



#### Color diff in two columns

    sdiff -w 230 <file 1> <file 2> | colordiff | less -r
