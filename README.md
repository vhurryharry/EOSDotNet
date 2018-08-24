﻿# EOSDotNet - EOS for enterprise

EOS Dot Net is cross plaform .NET core library intented to make interacting with the EOS blockchain (https://eos.io/) a pleasure. 

As much as possible the library tries to provide strongly typed classes which mirror the EOS structure. This helps to prevent runtime exceptions and provides excellent code completion and improved developer usability. 

The library is still under development, but currently provides a well structured framework for interacting with the system tables like the producers, voters, namebids, etc. 

Complexity such as pagination when dealing with tables is currently handled for the user. 

Plans are to expand the library to support all functions that are currently available through the cleos commandline tool. 

If you're a .NET develiper and would like to contribute to the project, we'd welcome all contributions. 


## What's in the box?

This repository currently contains three projects:

* **EOSDotNet** - This the library which can be included into your own project to build great things.  

* **cscleos** - This is an example project which makes use of the EOSDotNet class library. The commandline tool allows users to query system tables on the EOS Blockchain easily. As functionality is added to the EOSDotNet class library, this tool will expanded with useful features that leverage those functions. 

* **EOSLibConsole** - A scratch pad with some test which don't yet fit into the cscleos tool.

### cscleos

Simply running cscleos will output help that looks something like this:

```
Usage - cscleos <action> -options

GlobalOption   Description
Help (-?)      Shows this help

Actions

  getKnownTable <table> <outputFormat> [<fieldList>] [<delimiter>]  - Retrieve data from one of the well known EOS tables

    Option               Description
    table* (-t)          The name of the table
                         producers
                         voters
                         global
                         namebids
    outputFormat* (-o)   The format of the result. Defaults to Tab Seperated [Default='csv']
                         csv
                         json
    delimiter (-d)       The characted to use as a delimiter when outputting as a CSV. Default is a tab. [Default='     ']
    fieldList (-f)       A comma separated list of fields that should be returned. Default is to return all fields.
```

Example usage:

```
#By default the output is in TSV format. 
cscleos.exe getKnownTable namebids

#Specify -o json to output in json format
cscleos.exe getKnownTable namebids -o json

#Specify -d , to get the output in a csv format (comma is used as the delimiter as apposed to the default tab)
cscleos.exe getKnownTable namebids -d ,

#If you're only interested in specific fields, specify the -f and then provide a comma separated list of fields that you would like included.
cscleos.exe getKnownTable namebids -f newname,high_bid

```

Fetch all producers

```
# An example fetching all producers into a CSV
# cscleos.exe getKnownTable producers -d ,  | more

owner,total_votes,producer_key,is_active,unpaid_blocks,url,total_votes_long
123singapore,9680982131305682.00000000000000000,EOS71UbkZzuz55WNBpsEVQzkXrZAJ2XyLoQiEcS9WKwbYambhFxWb,True,0,http://eos.vote,9.68098213130568E+15
1eosbattles1,329144938830.10693359375000000,EOS1111111111111111111111111111111114T1Anm,False,0,http://eosbattles.com,329144938830.107
1eostheworld,7127308523679749.00000000000000000,EOS7DtVzfmr1c5ACb7usAwyn4f39V7urk6kBWswUWCtg3H8H6CFAr,True,0,https://eostheworld.io,7.12730852367975E+15
1teamcanada1,97028173128.15544128417968750,EOS7gBHpJMaWo8uzcXRfBAhN9yLfVTLTbH4L2xA64B5HNMnZpVuKJ,True,0,http://can-play.ca,97028173128.1554
acroeos12345,26187829550021016.00000000000000000,EOS56PyKoHXwyRkwDzr2uNhgDRioPoq5TwdN8Pm2hQGko7jrup2W5,True,0,http://www.acroeos.one,2.6187829550021E+16
activeeoscom,434395878933955.00000000000000000,EOS788SrVzZ3mJt3WUZkmYadjFJCisJGhZRTp85EznxEaqsARN26w,True,0,https://www.activeeos.com,434395878933955
alohaeosprod,5816532095666617.00000000000000000,EOS53pfXfxZ4tH3EGccdnGvBZVJsrcSf2nbCKiLLMphgaii9XxxhM,True,0,https://www.alohaeos.com,5.81653209566662E+15
argentinaeos,169687487348078496.00000000000000000,EOS7n4UUEDQRWeJ5UmCf9yqWXY5fsTtbo78HyYa5uBbM1xwa5DwRj,True,5522,https://www.eosargentina.io,1.69687487348078E+17
atticlabeosb,42191177849587144.00000000000000000,EOS7LqudX6Ac4woGwTF9CvQKwrJhg3H7p3pScDoXj1Ws82mMZFQqf,True,0,http://atticlab.net/,4.21911778495871E+16
atticlabeosp,13342565292388.24609375000000000,EOS1111111111111111111111111111111114T1Anm,False,0,http://atticlab.net/,13342565292388.2
aus1genereos,86798290100405904.00000000000000000,EOS57ZyzVjoEG2bvzmYmmeiH8YnYtRudxNKxppx17q7Hg29F8tW4t,True,0,http://www.genereos.io,8.67982901004059E+16
bchainlabeos,1054617659343577.37500000000000000,EOS6n6RZi6EXHKBX53HyuXgzMw5sUzWWQomwDLYLc1PcjZY3CCzzE,True,0,https://blockchainlab.me,1.05461765934358E+15
bitcoineosfu,13385780843681.28320312500000000,EOS5KvXdnwJV4YGcv7XL3K4UKsDSZxA13gmubYLTvE14g9vrMf7iT,True,0,http://bitcoineos.fun,13385780843681.3
bitcoingod11,26871852551978.96484375000000000,EOS8FGBXiineqciyhjKM2ypFgETDu8BJTDyHXuA2kY58Rbt1RNeHm,True,0,https://eos.bitcoingod.org/,26871852551979
bitfinexeos1,191486379979670112.00000000000000000,EOS6sgKjHUFtY1XxxQaMDwfxBac6nDBibVzZHb8LFMVmvSjcCdDhE,True,6247,https://www.bitfinex.com,1.9148637997967E+17
bitspacenode,16823859142716942.00000000000000000,EOS7HvfCTxaL4DwokbZRsbrXXQafzE6wcG38azf6WefKGHBqsE3Ad,True,0,https://eos.bitspace.no,1.68238591427169E+16
```

### EOSDotNet

Usage of the library is extremly simple. 

In the below example:
- HOST = {The URI of the API Endpoint}
- TABLE_ROW_TYPE = This is a class definitiion of the table you're interested in. 

```
var result = new EOS_Table<TABLE_ROW_TYPE>(HOST).GetRowsFromAPIAsync().Result;
```

Example working with the result
```

var producers = new EOS_Table<ProducerRow>(HOST).GetRowsFromAPIAsync().Result;
foreach (var _producer in producers)
{
    string line = string.Format("{0}\t{1}\t{2}\t{3}\t{4}", _producer.owner, _producer.total_votes, _producer.is_active, _producer.unpaid_blocks, _producer.url);
    logger.Debug(line);
}

```



## Installation



1. Install .NET core on your OS (Yes, this really works on Linux, and macOS) - easy to follow instructions can be found here
https://www.microsoft.com/net/learn/get-started

2. Clone the repo
```
git clone https://github.com/eosnewyork/EOSDotNet.git
cd EOSDotNet
```

Execute one of the following commands to create binaries:

```
dotnet publish -c release -r win10-x64
dotnet publish -c release -r osx.10.10-x64
dotnet publish -c release -r ubuntu.14.04-x64
```
Output will differ based on your system. Here's some example output from Ubuntu

```
$dotnet publish -c release -r ubuntu.14.04-x64
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restoring packages for /home/ubuntu/test1/EOSDotNet/EOSDotNet/EOSDotNet.csproj...
  Generating MSBuild file /home/ubuntu/test1/EOSDotNet/EOSDotNet/obj/EOSDotNet.csproj.nuget.g.props.
  Generating MSBuild file /home/ubuntu/test1/EOSDotNet/EOSDotNet/obj/EOSDotNet.csproj.nuget.g.targets.
  Restore completed in 253.11 ms for /home/ubuntu/test1/EOSDotNet/EOSDotNet/EOSDotNet.csproj.
  Restoring packages for /home/ubuntu/test1/EOSDotNet/cscleos/cscleos.csproj...
  Generating MSBuild file /home/ubuntu/test1/EOSDotNet/cscleos/obj/cscleos.csproj.nuget.g.props.
  Generating MSBuild file /home/ubuntu/test1/EOSDotNet/cscleos/obj/cscleos.csproj.nuget.g.targets.
  Restore completed in 51.47 ms for /home/ubuntu/test1/EOSDotNet/cscleos/cscleos.csproj.
  Restoring packages for /home/ubuntu/test1/EOSDotNet/EOSLibConsole/EOSLibConsole.csproj...
  Generating MSBuild file /home/ubuntu/test1/EOSDotNet/EOSLibConsole/obj/EOSLibConsole.csproj.nuget.g.props.
  Generating MSBuild file /home/ubuntu/test1/EOSDotNet/EOSLibConsole/obj/EOSLibConsole.csproj.nuget.g.targets.
  Restore completed in 23.63 ms for /home/ubuntu/test1/EOSDotNet/EOSLibConsole/EOSLibConsole.csproj.
  EOSDotNet -> /home/ubuntu/test1/EOSDotNet/EOSDotNet/bin/Release/netcoreapp2.1/EOSDotNet.dll
  EOSDotNet -> /home/ubuntu/test1/EOSDotNet/EOSDotNet/bin/Release/netcoreapp2.1/ubuntu.14.04-x64/EOSDotNet.dll
  EOSDotNet -> /home/ubuntu/test1/EOSDotNet/EOSDotNet/bin/Release/netcoreapp2.1/ubuntu.14.04-x64/publish/
  EOSLibConsole -> /home/ubuntu/test1/EOSDotNet/EOSLibConsole/bin/Release/netcoreapp2.1/ubuntu.14.04-x64/EOSLibConsole.dll
  EOSLibConsole -> /home/ubuntu/test1/EOSDotNet/EOSLibConsole/bin/Release/netcoreapp2.1/ubuntu.14.04-x64/publish/
  cscleos -> /home/ubuntu/test1/EOSDotNet/cscleos/bin/Release/netcoreapp2.1/ubuntu.14.04-x64/cscleos.dll
  cscleos -> /home/ubuntu/test1/EOSDotNet/cscleos/bin/Release/netcoreapp2.1/ubuntu.14.04-x64/publish/

```

```
# Change directly to the cscleos publish folder
cd cscleos/bin/Release/netcoreapp2.1/ubuntu.14.04-x64/publish/
#Run the cscleos without params to print the help
./cscleos 
```
