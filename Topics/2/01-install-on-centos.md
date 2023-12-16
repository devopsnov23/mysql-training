## MySQL Installation on Centos

### Installation Steps
1. Download the MySQL RPM bundle tar file from the MySQL Community Server downloads page.
```
[cloud_user_p_0c00f415@centos ~]$ sudo yum install mysql-server
CentOS Stream 8 - AppStream                                                                                                 556 kB/s |  35 MB     01:03    
CentOS Stream 8 - BaseOS                                                                                                     18 MB/s |  56 MB     00:03    
CentOS Stream 8 - Extras                                                                                                     68 kB/s |  18 kB     00:00    
CentOS Stream 8 - Extras common packages                                                                                     19 kB/s | 6.9 kB     00:00    
Google Compute Engine                                                                                                        28 kB/s |  11 kB     00:00    
Google Cloud SDK                                                                                                             30 MB/s | 147 MB     00:04    
Dependencies resolved.
============================================================================================================================================================
 Package                                      Architecture           Version                                                Repository                 Size
============================================================================================================================================================
Installing:
 mysql-server                                 x86_64                 8.0.26-1.module_el8.4.0+915+de215114                   appstream                  25 M
Installing dependencies:
 checkpolicy                                  x86_64                 2.9-1.el8                                              baseos                    348 k
 libaio                                       x86_64                 0.3.112-1.el8                                          baseos                     33 k
 mariadb-connector-c-config                   noarch                 3.1.11-2.el8_3                                         appstream                  15 k
 mecab                                        x86_64                 0.996-1.module_el8.4.0+589+11e12751.9                  appstream                 393 k
 mysql                                        x86_64                 8.0.26-1.module_el8.4.0+915+de215114                   appstream                  12 M
 mysql-common                                 x86_64                 8.0.26-1.module_el8.4.0+915+de215114                   appstream                 134 k
 mysql-errmsg                                 x86_64                 8.0.26-1.module_el8.4.0+915+de215114                   appstream                 598 k
 perl-Carp                                    noarch                 1.42-396.el8                                           baseos                     30 k
 perl-Data-Dumper                             x86_64                 2.167-399.el8                                          baseos                     58 k
 perl-Digest                                  noarch                 1.17-395.el8                                           appstream                  27 k
 perl-Digest-MD5                              x86_64                 2.55-396.el8                                           appstream                  37 k
 perl-Encode                                  x86_64                 4:2.97-3.el8                                           baseos                    1.5 M
 perl-Errno                                   x86_64                 1.28-422.el8                                           baseos                     76 k
 perl-Exporter                                noarch                 5.72-396.el8                                           baseos                     34 k
 perl-File-Path                               noarch                 2.15-2.el8                                             baseos                     38 k
 perl-File-Temp                               noarch                 0.230.600-1.el8                                        baseos                     63 k
 perl-Getopt-Long                             noarch                 1:2.50-4.el8                                           baseos                     63 k
 perl-HTTP-Tiny                               noarch                 0.074-2.el8                                            baseos                     58 k
 perl-IO                                      x86_64                 1.38-422.el8                                           baseos                    142 k
 perl-IO-Socket-IP                            noarch                 0.39-5.el8                                             appstream                  47 k
 perl-IO-Socket-SSL                           noarch                 2.066-4.module_el8+339+1ec643e0                        appstream                 304 k
 perl-MIME-Base64                             x86_64                 3.15-396.el8                                           baseos                     31 k
 perl-Mozilla-CA                              noarch                 20160104-7.module_el8+645+9d809f8c                     appstream                  15 k
 perl-Net-SSLeay                              x86_64                 1.88-2.module_el8+339+1ec643e0                         appstream                 402 k
 perl-PathTools                               x86_64                 3.74-1.el8                                             baseos                     90 k
 perl-Pod-Escapes                             noarch                 1:1.07-395.el8                                         baseos                     20 k
 perl-Pod-Perldoc                             noarch                 3.28-396.el8                                           baseos                     86 k
 perl-Pod-Simple                              noarch                 1:3.35-395.el8                                         baseos                    213 k
 perl-Pod-Usage                               noarch                 4:1.69-395.el8                                         baseos                     34 k
 perl-Scalar-List-Utils                       x86_64                 3:1.49-2.el8                                           baseos                     68 k
 perl-Socket                                  x86_64                 4:2.027-3.el8                                          baseos                     59 k
 perl-Storable                                x86_64                 1:3.11-3.el8                                           baseos                     98 k
 perl-Term-ANSIColor                          noarch                 4.06-396.el8                                           baseos                     46 k
 perl-Term-Cap                                noarch                 1.17-395.el8                                           baseos                     23 k
 perl-Text-ParseWords                         noarch                 3.30-395.el8                                           baseos                     18 k
 perl-Text-Tabs+Wrap                          noarch                 2013.0523-395.el8                                      baseos                     24 k
 perl-Time-Local                              noarch                 1:1.280-1.el8                                          baseos                     34 k
 perl-URI                                     noarch                 1.73-3.el8                                             appstream                 116 k
 perl-Unicode-Normalize                       x86_64                 1.25-396.el8                                           baseos                     82 k
 perl-constant                                noarch                 1.33-396.el8                                           baseos                     25 k
 perl-interpreter                             x86_64                 4:5.26.3-422.el8                                       baseos                    6.3 M
 perl-libnet                                  noarch                 3.11-3.el8                                             appstream                 121 k
 perl-libs                                    x86_64                 4:5.26.3-422.el8                                       baseos                    1.6 M
 perl-macros                                  x86_64                 4:5.26.3-422.el8                                       baseos                     73 k
 perl-parent                                  noarch                 1:0.237-1.el8                                          baseos                     20 k
 perl-podlators                               noarch                 4.11-1.el8                                             baseos                    118 k
 perl-threads                                 x86_64                 1:2.21-2.el8                                           baseos                     61 k
 perl-threads-shared                          x86_64                 1.58-2.el8                                             baseos                     48 k
 policycoreutils-python-utils                 noarch                 2.9-24.el8                                             baseos                    260 k
 protobuf-lite                                x86_64                 3.5.0-15.el8                                           appstream                 149 k
 python3-audit                                x86_64                 3.1.2-1.el8                                            baseos                     88 k
 python3-libsemanage                          x86_64                 2.9-9.el8                                              baseos                    128 k
 python3-policycoreutils                      noarch                 2.9-24.el8                                             baseos                    2.3 M
 python3-setools                              x86_64                 4.3.0-5.el8                                            baseos                    627 k
Enabling module streams:
 mysql                                                               8.0                                                                                   
 perl                                                                5.26                                                                                  
 perl-IO-Socket-SSL                                                  2.066                                                                                 
 perl-libwww-perl                                                    6.34                                                                                  

Transaction Summary
============================================================================================================================================================
Install  55 Packages

Total download size: 54 M
Installed size: 241 M
Is this ok [y/N]: y
Downloading Packages:
(1/55): mariadb-connector-c-config-3.1.11-2.el8_3.noarch.rpm                                                                 76 kB/s |  15 kB     00:00    
(2/55): mecab-0.996-1.module_el8.4.0+589+11e12751.9.x86_64.rpm                                                              1.1 MB/s | 393 kB     00:00    
(3/55): mysql-common-8.0.26-1.module_el8.4.0+915+de215114.x86_64.rpm                                                        758 kB/s | 134 kB     00:00    
(4/55): mysql-errmsg-8.0.26-1.module_el8.4.0+915+de215114.x86_64.rpm                                                        5.3 MB/s | 598 kB     00:00    
(5/55): perl-Digest-1.17-395.el8.noarch.rpm                                                                                 575 kB/s |  27 kB     00:00    
(6/55): perl-Digest-MD5-2.55-396.el8.x86_64.rpm                                                                             785 kB/s |  37 kB     00:00    
(7/55): perl-IO-Socket-IP-0.39-5.el8.noarch.rpm                                                                             988 kB/s |  47 kB     00:00    
(8/55): mysql-8.0.26-1.module_el8.4.0+915+de215114.x86_64.rpm                                                                15 MB/s |  12 MB     00:00    
(9/55): perl-IO-Socket-SSL-2.066-4.module_el8+339+1ec643e0.noarch.rpm                                                       1.6 MB/s | 304 kB     00:00    
(10/55): perl-Mozilla-CA-20160104-7.module_el8+645+9d809f8c.noarch.rpm                                                      325 kB/s |  15 kB     00:00    
(11/55): perl-Net-SSLeay-1.88-2.module_el8+339+1ec643e0.x86_64.rpm                                                          6.0 MB/s | 402 kB     00:00    
(12/55): perl-URI-1.73-3.el8.noarch.rpm                                                                                     2.3 MB/s | 116 kB     00:00    
(13/55): perl-libnet-3.11-3.el8.noarch.rpm                                                                                  2.3 MB/s | 121 kB     00:00    
(14/55): protobuf-lite-3.5.0-15.el8.x86_64.rpm                                                                              2.5 MB/s | 149 kB     00:00    
(15/55): libaio-0.3.112-1.el8.x86_64.rpm                                                                                    283 kB/s |  33 kB     00:00    
(16/55): perl-Carp-1.42-396.el8.noarch.rpm                                                                                  850 kB/s |  30 kB     00:00    
(17/55): mysql-server-8.0.26-1.module_el8.4.0+915+de215114.x86_64.rpm                                                        25 MB/s |  25 MB     00:00    
(18/55): perl-Data-Dumper-2.167-399.el8.x86_64.rpm                                                                          215 kB/s |  58 kB     00:00    
(19/55): checkpolicy-2.9-1.el8.x86_64.rpm                                                                                   757 kB/s | 348 kB     00:00    
(20/55): perl-Errno-1.28-422.el8.x86_64.rpm                                                                                 2.0 MB/s |  76 kB     00:00    
(21/55): perl-Exporter-5.72-396.el8.noarch.rpm                                                                              956 kB/s |  34 kB     00:00    
(22/55): perl-File-Path-2.15-2.el8.noarch.rpm                                                                               1.0 MB/s |  38 kB     00:00    
(23/55): perl-File-Temp-0.230.600-1.el8.noarch.rpm                                                                          1.7 MB/s |  63 kB     00:00    
(24/55): perl-Getopt-Long-2.50-4.el8.noarch.rpm                                                                             1.7 MB/s |  63 kB     00:00    
(25/55): perl-HTTP-Tiny-0.074-2.el8.noarch.rpm                                                                              1.6 MB/s |  58 kB     00:00    
(26/55): perl-IO-1.38-422.el8.x86_64.rpm                                                                                    3.8 MB/s | 142 kB     00:00    
(27/55): perl-MIME-Base64-3.15-396.el8.x86_64.rpm                                                                           835 kB/s |  31 kB     00:00    
(28/55): perl-PathTools-3.74-1.el8.x86_64.rpm                                                                               2.4 MB/s |  90 kB     00:00    
(29/55): perl-Pod-Escapes-1.07-395.el8.noarch.rpm                                                                           560 kB/s |  20 kB     00:00    
(30/55): perl-Pod-Perldoc-3.28-396.el8.noarch.rpm                                                                           2.3 MB/s |  86 kB     00:00    
(31/55): perl-Pod-Usage-1.69-395.el8.noarch.rpm                                                                             973 kB/s |  34 kB     00:00    
(32/55): perl-Pod-Simple-3.35-395.el8.noarch.rpm                                                                            2.8 MB/s | 213 kB     00:00    
(33/55): perl-Encode-2.97-3.el8.x86_64.rpm                                                                                  5.0 MB/s | 1.5 MB     00:00    
(34/55): perl-Scalar-List-Utils-1.49-2.el8.x86_64.rpm                                                                       1.9 MB/s |  68 kB     00:00    
(35/55): perl-Socket-2.027-3.el8.x86_64.rpm                                                                                 1.6 MB/s |  59 kB     00:00    
(36/55): perl-Storable-3.11-3.el8.x86_64.rpm                                                                                2.6 MB/s |  98 kB     00:00    
(37/55): perl-Term-ANSIColor-4.06-396.el8.noarch.rpm                                                                        1.2 MB/s |  46 kB     00:00    
(38/55): perl-Term-Cap-1.17-395.el8.noarch.rpm                                                                              662 kB/s |  23 kB     00:00    
(39/55): perl-Text-ParseWords-3.30-395.el8.noarch.rpm                                                                       508 kB/s |  18 kB     00:00    
(40/55): perl-Text-Tabs+Wrap-2013.0523-395.el8.noarch.rpm                                                                   687 kB/s |  24 kB     00:00    
(41/55): perl-Time-Local-1.280-1.el8.noarch.rpm                                                                             948 kB/s |  34 kB     00:00    
(42/55): perl-Unicode-Normalize-1.25-396.el8.x86_64.rpm                                                                     2.2 MB/s |  82 kB     00:00    
(43/55): perl-constant-1.33-396.el8.noarch.rpm                                                                              700 kB/s |  25 kB     00:00    
(44/55): perl-macros-5.26.3-422.el8.x86_64.rpm                                                                              2.0 MB/s |  73 kB     00:00    
(45/55): perl-parent-0.237-1.el8.noarch.rpm                                                                                 568 kB/s |  20 kB     00:00    
(46/55): perl-libs-5.26.3-422.el8.x86_64.rpm                                                                                 18 MB/s | 1.6 MB     00:00    
(47/55): perl-podlators-4.11-1.el8.noarch.rpm                                                                               3.1 MB/s | 118 kB     00:00    
(48/55): perl-threads-2.21-2.el8.x86_64.rpm                                                                                 1.7 MB/s |  61 kB     00:00    
(49/55): perl-threads-shared-1.58-2.el8.x86_64.rpm                                                                          1.3 MB/s |  48 kB     00:00    
(50/55): policycoreutils-python-utils-2.9-24.el8.noarch.rpm                                                                 6.6 MB/s | 260 kB     00:00    
(51/55): perl-interpreter-5.26.3-422.el8.x86_64.rpm                                                                          23 MB/s | 6.3 MB     00:00    
(52/55): python3-audit-3.1.2-1.el8.x86_64.rpm                                                                               903 kB/s |  88 kB     00:00    
(53/55): python3-libsemanage-2.9-9.el8.x86_64.rpm                                                                           1.4 MB/s | 128 kB     00:00    
(54/55): python3-policycoreutils-2.9-24.el8.noarch.rpm                                                                       42 MB/s | 2.3 MB     00:00    
(55/55): python3-setools-4.3.0-5.el8.x86_64.rpm                                                                             8.0 MB/s | 627 kB     00:00    
------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                        24 MB/s |  54 MB     00:02     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                                                    1/1 
  Installing       : mariadb-connector-c-config-3.1.11-2.el8_3.noarch                                                                                  1/55 
  Installing       : mysql-common-8.0.26-1.module_el8.4.0+915+de215114.x86_64                                                                          2/55 
  Installing       : mysql-8.0.26-1.module_el8.4.0+915+de215114.x86_64                                                                                 3/55 
  Installing       : mysql-errmsg-8.0.26-1.module_el8.4.0+915+de215114.x86_64                                                                          4/55 
  Installing       : perl-Digest-1.17-395.el8.noarch                                                                                                   5/55 
  Installing       : perl-Digest-MD5-2.55-396.el8.x86_64                                                                                               6/55 
  Installing       : perl-Data-Dumper-2.167-399.el8.x86_64                                                                                             7/55 
  Installing       : perl-libnet-3.11-3.el8.noarch                                                                                                     8/55 
  Installing       : perl-URI-1.73-3.el8.noarch                                                                                                        9/55 
  Installing       : perl-Pod-Escapes-1:1.07-395.el8.noarch                                                                                           10/55 
  Installing       : perl-Net-SSLeay-1.88-2.module_el8+339+1ec643e0.x86_64                                                                            11/55 
  Installing       : perl-Mozilla-CA-20160104-7.module_el8+645+9d809f8c.noarch                                                                        12/55 
  Installing       : perl-IO-Socket-IP-0.39-5.el8.noarch                                                                                              13/55 
  Installing       : perl-Time-Local-1:1.280-1.el8.noarch                                                                                             14/55 
  Installing       : perl-IO-Socket-SSL-2.066-4.module_el8+339+1ec643e0.noarch                                                                        15/55 
  Installing       : perl-Term-ANSIColor-4.06-396.el8.noarch                                                                                          16/55 
  Installing       : perl-Term-Cap-1.17-395.el8.noarch                                                                                                17/55 
  Installing       : perl-File-Temp-0.230.600-1.el8.noarch                                                                                            18/55 
  Installing       : perl-Pod-Simple-1:3.35-395.el8.noarch                                                                                            19/55 
  Installing       : perl-HTTP-Tiny-0.074-2.el8.noarch                                                                                                20/55 
  Installing       : perl-podlators-4.11-1.el8.noarch                                                                                                 21/55 
  Installing       : perl-Pod-Perldoc-3.28-396.el8.noarch                                                                                             22/55 
  Installing       : perl-Text-ParseWords-3.30-395.el8.noarch                                                                                         23/55 
  Installing       : perl-Pod-Usage-4:1.69-395.el8.noarch                                                                                             24/55 
  Installing       : perl-MIME-Base64-3.15-396.el8.x86_64                                                                                             25/55 
  Installing       : perl-Storable-1:3.11-3.el8.x86_64                                                                                                26/55 
  Installing       : perl-Getopt-Long-1:2.50-4.el8.noarch                                                                                             27/55 
  Installing       : perl-Errno-1.28-422.el8.x86_64                                                                                                   28/55 
  Installing       : perl-Socket-4:2.027-3.el8.x86_64                                                                                                 29/55 
  Installing       : perl-Encode-4:2.97-3.el8.x86_64                                                                                                  30/55 
  Installing       : perl-Carp-1.42-396.el8.noarch                                                                                                    31/55 
  Installing       : perl-Exporter-5.72-396.el8.noarch                                                                                                32/55 
  Installing       : perl-libs-4:5.26.3-422.el8.x86_64                                                                                                33/55 
  Installing       : perl-Scalar-List-Utils-3:1.49-2.el8.x86_64                                                                                       34/55 
  Installing       : perl-parent-1:0.237-1.el8.noarch                                                                                                 35/55 
  Installing       : perl-macros-4:5.26.3-422.el8.x86_64                                                                                              36/55 
  Installing       : perl-Text-Tabs+Wrap-2013.0523-395.el8.noarch                                                                                     37/55 
  Installing       : perl-Unicode-Normalize-1.25-396.el8.x86_64                                                                                       38/55 
  Installing       : perl-File-Path-2.15-2.el8.noarch                                                                                                 39/55 
  Installing       : perl-IO-1.38-422.el8.x86_64                                                                                                      40/55 
  Installing       : perl-PathTools-3.74-1.el8.x86_64                                                                                                 41/55 
  Installing       : perl-constant-1.33-396.el8.noarch                                                                                                42/55 
  Installing       : perl-threads-1:2.21-2.el8.x86_64                                                                                                 43/55 
  Installing       : perl-threads-shared-1.58-2.el8.x86_64                                                                                            44/55 
  Installing       : perl-interpreter-4:5.26.3-422.el8.x86_64                                                                                         45/55 
  Installing       : python3-setools-4.3.0-5.el8.x86_64                                                                                               46/55 
  Installing       : python3-libsemanage-2.9-9.el8.x86_64                                                                                             47/55 
  Installing       : python3-audit-3.1.2-1.el8.x86_64                                                                                                 48/55 
  Installing       : libaio-0.3.112-1.el8.x86_64                                                                                                      49/55 
  Installing       : checkpolicy-2.9-1.el8.x86_64                                                                                                     50/55 
  Installing       : python3-policycoreutils-2.9-24.el8.noarch                                                                                        51/55 
  Installing       : policycoreutils-python-utils-2.9-24.el8.noarch                                                                                   52/55 
  Installing       : protobuf-lite-3.5.0-15.el8.x86_64                                                                                                53/55 
  Installing       : mecab-0.996-1.module_el8.4.0+589+11e12751.9.x86_64                                                                               54/55 
  Running scriptlet: mecab-0.996-1.module_el8.4.0+589+11e12751.9.x86_64                                                                               54/55 
  Running scriptlet: mysql-server-8.0.26-1.module_el8.4.0+915+de215114.x86_64                                                                         55/55 
  Installing       : mysql-server-8.0.26-1.module_el8.4.0+915+de215114.x86_64                                                                         55/55 
  Running scriptlet: mysql-server-8.0.26-1.module_el8.4.0+915+de215114.x86_64                                                                         55/55 
ValueError: File context for /var/log/mysql(/.*)? already defined

  Verifying        : mariadb-connector-c-config-3.1.11-2.el8_3.noarch                                                                                  1/55 
  Verifying        : mecab-0.996-1.module_el8.4.0+589+11e12751.9.x86_64                                                                                2/55 
  Verifying        : mysql-8.0.26-1.module_el8.4.0+915+de215114.x86_64                                                                                 3/55 
  Verifying        : mysql-common-8.0.26-1.module_el8.4.0+915+de215114.x86_64                                                                          4/55 
  Verifying        : mysql-errmsg-8.0.26-1.module_el8.4.0+915+de215114.x86_64                                                                          5/55 
  Verifying        : mysql-server-8.0.26-1.module_el8.4.0+915+de215114.x86_64                                                                          6/55 
  Verifying        : perl-Digest-1.17-395.el8.noarch                                                                                                   7/55 
  Verifying        : perl-Digest-MD5-2.55-396.el8.x86_64                                                                                               8/55 
  Verifying        : perl-IO-Socket-IP-0.39-5.el8.noarch                                                                                               9/55 
  Verifying        : perl-IO-Socket-SSL-2.066-4.module_el8+339+1ec643e0.noarch                                                                        10/55 
  Verifying        : perl-Mozilla-CA-20160104-7.module_el8+645+9d809f8c.noarch                                                                        11/55 
  Verifying        : perl-Net-SSLeay-1.88-2.module_el8+339+1ec643e0.x86_64                                                                            12/55 
  Verifying        : perl-URI-1.73-3.el8.noarch                                                                                                       13/55 
  Verifying        : perl-libnet-3.11-3.el8.noarch                                                                                                    14/55 
  Verifying        : protobuf-lite-3.5.0-15.el8.x86_64                                                                                                15/55 
  Verifying        : checkpolicy-2.9-1.el8.x86_64                                                                                                     16/55 
  Verifying        : libaio-0.3.112-1.el8.x86_64                                                                                                      17/55 
  Verifying        : perl-Carp-1.42-396.el8.noarch                                                                                                    18/55 
  Verifying        : perl-Data-Dumper-2.167-399.el8.x86_64                                                                                            19/55 
  Verifying        : perl-Encode-4:2.97-3.el8.x86_64                                                                                                  20/55 
  Verifying        : perl-Errno-1.28-422.el8.x86_64                                                                                                   21/55 
  Verifying        : perl-Exporter-5.72-396.el8.noarch                                                                                                22/55 
  Verifying        : perl-File-Path-2.15-2.el8.noarch                                                                                                 23/55 
  Verifying        : perl-File-Temp-0.230.600-1.el8.noarch                                                                                            24/55 
  Verifying        : perl-Getopt-Long-1:2.50-4.el8.noarch                                                                                             25/55 
  Verifying        : perl-HTTP-Tiny-0.074-2.el8.noarch                                                                                                26/55 
  Verifying        : perl-IO-1.38-422.el8.x86_64                                                                                                      27/55 
  Verifying        : perl-MIME-Base64-3.15-396.el8.x86_64                                                                                             28/55 
  Verifying        : perl-PathTools-3.74-1.el8.x86_64                                                                                                 29/55 
  Verifying        : perl-Pod-Escapes-1:1.07-395.el8.noarch                                                                                           30/55 
  Verifying        : perl-Pod-Perldoc-3.28-396.el8.noarch                                                                                             31/55 
  Verifying        : perl-Pod-Simple-1:3.35-395.el8.noarch                                                                                            32/55 
  Verifying        : perl-Pod-Usage-4:1.69-395.el8.noarch                                                                                             33/55 
  Verifying        : perl-Scalar-List-Utils-3:1.49-2.el8.x86_64                                                                                       34/55 
  Verifying        : perl-Socket-4:2.027-3.el8.x86_64                                                                                                 35/55 
  Verifying        : perl-Storable-1:3.11-3.el8.x86_64                                                                                                36/55 
  Verifying        : perl-Term-ANSIColor-4.06-396.el8.noarch                                                                                          37/55 
  Verifying        : perl-Term-Cap-1.17-395.el8.noarch                                                                                                38/55 
  Verifying        : perl-Text-ParseWords-3.30-395.el8.noarch                                                                                         39/55 
  Verifying        : perl-Text-Tabs+Wrap-2013.0523-395.el8.noarch                                                                                     40/55 
  Verifying        : perl-Time-Local-1:1.280-1.el8.noarch                                                                                             41/55 
  Verifying        : perl-Unicode-Normalize-1.25-396.el8.x86_64                                                                                       42/55 
  Verifying        : perl-constant-1.33-396.el8.noarch                                                                                                43/55 
  Verifying        : perl-interpreter-4:5.26.3-422.el8.x86_64                                                                                         44/55 
  Verifying        : perl-libs-4:5.26.3-422.el8.x86_64                                                                                                45/55 
  Verifying        : perl-macros-4:5.26.3-422.el8.x86_64                                                                                              46/55 
  Verifying        : perl-parent-1:0.237-1.el8.noarch                                                                                                 47/55 
  Verifying        : perl-podlators-4.11-1.el8.noarch                                                                                                 48/55 
  Verifying        : perl-threads-1:2.21-2.el8.x86_64                                                                                                 49/55 
  Verifying        : perl-threads-shared-1.58-2.el8.x86_64                                                                                            50/55 
  Verifying        : policycoreutils-python-utils-2.9-24.el8.noarch                                                                                   51/55 
  Verifying        : python3-audit-3.1.2-1.el8.x86_64                                                                                                 52/55 
  Verifying        : python3-libsemanage-2.9-9.el8.x86_64                                                                                             53/55 
  Verifying        : python3-policycoreutils-2.9-24.el8.noarch                                                                                        54/55 
  Verifying        : python3-setools-4.3.0-5.el8.x86_64                                                                                               55/55 

Installed:
  checkpolicy-2.9-1.el8.x86_64                                                 libaio-0.3.112-1.el8.x86_64                                                  
  mariadb-connector-c-config-3.1.11-2.el8_3.noarch                             mecab-0.996-1.module_el8.4.0+589+11e12751.9.x86_64                           
  mysql-8.0.26-1.module_el8.4.0+915+de215114.x86_64                            mysql-common-8.0.26-1.module_el8.4.0+915+de215114.x86_64                     
  mysql-errmsg-8.0.26-1.module_el8.4.0+915+de215114.x86_64                     mysql-server-8.0.26-1.module_el8.4.0+915+de215114.x86_64                     
  perl-Carp-1.42-396.el8.noarch                                                perl-Data-Dumper-2.167-399.el8.x86_64                                        
  perl-Digest-1.17-395.el8.noarch                                              perl-Digest-MD5-2.55-396.el8.x86_64                                          
  perl-Encode-4:2.97-3.el8.x86_64                                              perl-Errno-1.28-422.el8.x86_64                                               
  perl-Exporter-5.72-396.el8.noarch                                            perl-File-Path-2.15-2.el8.noarch                                             
  perl-File-Temp-0.230.600-1.el8.noarch                                        perl-Getopt-Long-1:2.50-4.el8.noarch                                         
  perl-HTTP-Tiny-0.074-2.el8.noarch                                            perl-IO-1.38-422.el8.x86_64                                                  
  perl-IO-Socket-IP-0.39-5.el8.noarch                                          perl-IO-Socket-SSL-2.066-4.module_el8+339+1ec643e0.noarch                    
  perl-MIME-Base64-3.15-396.el8.x86_64                                         perl-Mozilla-CA-20160104-7.module_el8+645+9d809f8c.noarch                    
  perl-Net-SSLeay-1.88-2.module_el8+339+1ec643e0.x86_64                        perl-PathTools-3.74-1.el8.x86_64                                             
  perl-Pod-Escapes-1:1.07-395.el8.noarch                                       perl-Pod-Perldoc-3.28-396.el8.noarch                                         
  perl-Pod-Simple-1:3.35-395.el8.noarch                                        perl-Pod-Usage-4:1.69-395.el8.noarch                                         
  perl-Scalar-List-Utils-3:1.49-2.el8.x86_64                                   perl-Socket-4:2.027-3.el8.x86_64                                             
  perl-Storable-1:3.11-3.el8.x86_64                                            perl-Term-ANSIColor-4.06-396.el8.noarch                                      
  perl-Term-Cap-1.17-395.el8.noarch                                            perl-Text-ParseWords-3.30-395.el8.noarch                                     
  perl-Text-Tabs+Wrap-2013.0523-395.el8.noarch                                 perl-Time-Local-1:1.280-1.el8.noarch                                         
  perl-URI-1.73-3.el8.noarch                                                   perl-Unicode-Normalize-1.25-396.el8.x86_64                                   
  perl-constant-1.33-396.el8.noarch                                            perl-interpreter-4:5.26.3-422.el8.x86_64                                     
  perl-libnet-3.11-3.el8.noarch                                                perl-libs-4:5.26.3-422.el8.x86_64                                            
  perl-macros-4:5.26.3-422.el8.x86_64                                          perl-parent-1:0.237-1.el8.noarch                                             
  perl-podlators-4.11-1.el8.noarch                                             perl-threads-1:2.21-2.el8.x86_64                                             
  perl-threads-shared-1.58-2.el8.x86_64                                        policycoreutils-python-utils-2.9-24.el8.noarch                               
  protobuf-lite-3.5.0-15.el8.x86_64                                            python3-audit-3.1.2-1.el8.x86_64                                             
  python3-libsemanage-2.9-9.el8.x86_64                                         python3-policycoreutils-2.9-24.el8.noarch                                    
  python3-setools-4.3.0-5.el8.x86_64                                          

Complete!
[cloud_user_p_0c00f415@centos ~]$
```
2. Enable and start mysqld service 
```
[cloud_user_p_0c00f415@centos ~]$ sudo systemctl enable mysqld 
Created symlink /etc/systemd/system/multi-user.target.wants/mysqld.service → /usr/lib/systemd/system/mysqld.service.
[cloud_user_p_0c00f415@centos ~]$ sudo systemctl start mysqld
[cloud_user_p_0c00f415@centos ~]$ sudo systemctl status mysqld
● mysqld.service - MySQL 8.0 database server
   Loaded: loaded (/usr/lib/systemd/system/mysqld.service; enabled; vendor preset: disabled)
   Active: active (running) since Sat 2023-12-16 14:37:07 UTC; 8s ago
  Process: 71063 ExecStartPost=/usr/libexec/mysql-check-upgrade (code=exited, status=0/SUCCESS)
  Process: 70934 ExecStartPre=/usr/libexec/mysql-prepare-db-dir mysqld.service (code=exited, status=0/SUCCESS)
  Process: 70910 ExecStartPre=/usr/libexec/mysql-check-socket (code=exited, status=0/SUCCESS)
 Main PID: 71017 (mysqld)
   Status: "Server is operational"
    Tasks: 38 (limit: 23184)
   Memory: 461.9M
   CGroup: /system.slice/mysqld.service
           └─71017 /usr/libexec/mysqld --basedir=/usr

Dec 16 14:37:00 centos systemd[1]: Starting MySQL 8.0 database server...
Dec 16 14:37:00 centos mysql-prepare-db-dir[70934]: Initializing MySQL database
Dec 16 14:37:07 centos systemd[1]: Started MySQL 8.0 database server.
[cloud_user_p_0c00f415@centos ~]$
```

3. Securing MySQL 
```
[cloud_user_p_0c00f415@centos ~]$ sudo mysql_secure_installation

Securing the MySQL server deployment.

Connecting to MySQL using a blank password.

VALIDATE PASSWORD COMPONENT can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD component?

Press y|Y for Yes, any other key for No: Y

There are three levels of password validation policy:

LOW    Length >= 8
MEDIUM Length >= 8, numeric, mixed case, and special characters
STRONG Length >= 8, numeric, mixed case, special characters and dictionary                  file

Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG: 2
Please set the password for root here.

New password: 

Re-enter new password: 

Estimated strength of the password: 25 
Do you wish to continue with the password provided?(Press y|Y for Yes, any other key for No) : Y
 ... Failed! Error: Your password does not satisfy the current policy requirements

New password: 

Re-enter new password: 

Estimated strength of the password: 100 
Do you wish to continue with the password provided?(Press y|Y for Yes, any other key for No) : Y
By default, a MySQL installation has an anonymous user,
allowing anyone to log into MySQL without having to have
a user account created for them. This is intended only for
testing, and to make the installation go a bit smoother.
You should remove them before moving into a production
environment.

Remove anonymous users? (Press y|Y for Yes, any other key for No) : Y
Success.


Normally, root should only be allowed to connect from
'localhost'. This ensures that someone cannot guess at
the root password from the network.

Disallow root login remotely? (Press y|Y for Yes, any other key for No) : Y
Success.

By default, MySQL comes with a database named 'test' that
anyone can access. This is also intended only for testing,
and should be removed before moving into a production
environment.


Remove test database and access to it? (Press y|Y for Yes, any other key for No) : Y
 - Dropping test database...
Success.

 - Removing privileges on test database...
Success.

Reloading the privilege tables will ensure that all changes
made so far will take effect immediately.

Reload privilege tables now? (Press y|Y for Yes, any other key for No) : Y
Success.

All done! 
[cloud_user_p_0c00f415@centos ~]$ 
```
4. Testing MySQL 
```
[cloud_user_p_0c00f415@centos ~]$ mysqladmin -u root -p version
Enter password: 
mysqladmin  Ver 8.0.26 for Linux on x86_64 (Source distribution)
Copyright (c) 2000, 2021, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Server version          8.0.26
Protocol version        10
Connection              Localhost via UNIX socket
UNIX socket             /var/lib/mysql/mysql.sock
Uptime:                 7 min 16 sec

Threads: 2  Questions: 16  Slow queries: 0  Opens: 133  Flush tables: 3  Open tables: 49  Queries per second avg: 0.036
[cloud_user_p_0c00f415@centos ~]$
```
