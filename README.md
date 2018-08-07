![image](https://i.imgur.com/yY6MDPm.png)

## What is ErrorCoin?

It is a quip in the blockchain system. Everything you know is now dead.


## Compile instructions

## Ubuntu

First, you need to download the dependencies of 42, pretty simple because Ubuntu has that neat package manager.
Heres the gist of what you need:

` sudo apt-get install -y build-essential python-dev gcc g++ git cmake libboost-all-dev librocksdb-dev libreadline-dev `


If you cant install librocksdb-dev on your version of Ubuntu, no sweat man, just add the repo via PPA:


```
sudo add-apt-repository ppa:ethcore/ethcore -y
sudo apt-get update
sudo apt-get install librocksdb-dev
```

Alright, now thats out of the way, its time to compile ErrorCoin!


```
git clone https://github.com/ErrorCoin/errorcoin.git
```
Then
```
cd errorcoin
mkdir build
cd build
cmake ..
```
Then 
```
make -j4
```
Boom! You made it :D
Also if you're having permision issues related to build_detect_platform and version.sh in external/rocksdb/build_tools, its a permissions thing. Do chmod +x to version.sh and build_detect_platform (or the whole folder if you like)

## Windows

Suprisingly enough, compiling ErrorCoin on Windows is actually not that hard! Its pretty simple, first just download the deps

You need [Visual Studio Community 2017](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&page=inlineinstall)
When downloading, make sure you install Desktop Development with C++ and the VC++ 140 Toolchain (should be on the right of the installer screen) in order to compile correctly.
You also need [Cmake](https://cmake.org/download/) in order to make the MSVC solution file.
And last but not least, you need the dreaded [Boost 1.59.0](https://sourceforge.net/projects/boost/files/boost-binaries/1.59.0/) Make sure to download the MSVC 14 installer version of boost!

Now to compile ErrorCoin!

In the x64 Native Tools Command prompt for Visual Studio 2017, go into the ErrorCoin folder
` cd <errorcoin-file-path `
Now, we need to make the MSVC solution file
` cmake -G "Visual Studio 14 Win64" -DBOOST_ROOT=C:/local/boost_1_59_0 CMakeLists.txt `
Once its down making the build files, simply run this command in the same directory:
` MSBuild errorcoin.sln /p:Configuration=Release /m `
Let it do its thing, and once it's done compiling go to /src/ and in the release folder the binaries will be there!

## Mac OSX

I currently don't have use of a Mac, perhaps someone could do this. Hopefully!
