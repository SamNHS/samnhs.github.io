# Requirements

- Ruby
- GCC
- Make
- zlib1g-dev (Linux, WSL)

These can be installed via apt on Linux/WSL (if Debian / Ubuntu based). For a minimal install of Linux, Debian is a good option.

```
wsl.exe --install Debian
```

You can launch WSL Debian using the command, when you first install it, it runs it by default.

```
wsl.exe -d Debian
```

Once Debian is installed, start WSL and apply updates.

```
sudo apt update && sudo apt upgrade -y
```

Then install Ruby (this will use nearly 450MB+ of storage).

```
sudo apt install ruby-full build-essential zlib1g-dev
```

Setup `.gem` folder so `sudo` isn't required.

```
export GEM_HOME=$HOME/.gem
source ~/.bashrc
```

To prevent the need to do this every time you start a WSL session, edit the `~/.bashrc` file.

```
nano ~/.bashrc
```

Add the following to the end of the file and save.

```
export GEM_HOME=$HOME/.gem
```

## Setting up and testing

Change to `docs` if you are not there already.

```
cd docs
```

Install the `bundler` gem (if you get errors when using the `bundle` command).

```
gem install bundler
```

Install required gems.

```
bundle install
```

Update gems if needed.

```
bundle update
```

Test with Jekyll.

```
bundle exec jekyll serve
```