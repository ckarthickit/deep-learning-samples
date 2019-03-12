# Deep Learning Starter

## Steps to Prepare Environment for DeepLearning on MAC

- Install Python 3.6.5

  ```bash
  https://raw.githubusercontent.com/Homebrew/homebrew-core/f2a764ef944b1080be64bd88dca9a1d80130c558/Formula/python.rb
  ```

  We might face the below error:

  ```bash
  Error: python contains a recursive dependency on itself:
  python depends on sphinx-doc
  sphinx-doc depends on python
  ```

  To fix this, we can do the following :

  ```bash
    #Unlink the symbolink links set by python that was previously installed using brew command
    brew unlink python

    #Install python using brew and --ignore-dependencies flag
    brew install --ignore-dependencies https://raw.githubusercontent.com/Homebrew/homebrew-core/f2a764ef944b1080be64bd88dca9a1d80130c558/Formula/python.rb
  ```

- Verify Python Install locations

  ```bash
     #type is a command that indicates how a "name" would be interpreted if used as a "command-name"
     # -a flag is used to display all of the places that contain the executable name.
     type -a python

     type -a ptyhon3
     # output :
     #python3 is /usr/local/bin/python3

     python3 -V
     #output:
     #Python 3.6.5
  ```

- Virtual Environment Packages

  *We would be installing packages `virtualenv` & `virtualenvwrapper`, which would enable us to create virtual environments and create projects within these virtual environments. Working on a python project would require many python packages to be installed. Virtual environments makes it easy to install and manage those packages within these environments and once we are done with the work we can delete the complete project, which deletes all the packages also. It is quite handy and helpful in managing packages.*

  - Install `virtualenv` and `virtualenvwrapper` using `pip3`

  ```bash
  #Installing virtualenv & virtualenvwrapper:
  #PIP is a package manager for Python packages, or modules if you like.
  pip3 install virtualenv virtualenvwrapper
  ```

  - Setup Bash Profile to include Environmental variables for `virtualenv` and `virtualenvwrapper`.

  ```bash
  export VIRTUALENVWRAPPER_PYTHON=/usr/local/bin/python3
  export WORKON_HOME=~/Envs
  source /usr/local/bin/virtualenvwrapper.sh
  ```

  - Test Virtual Environment Creation

  ```bash
  #Creating Virtual Environment for <myproject>
  mkvirtualenv -p python3 <myproject>
  #Output of `mkvirtualenv -p python3 hello`
  #Running virtualenv with interpreter /usr/local/bin/python3
  #Using base prefix '/usr/local/Cellar/python/3.6.5_1/Frameworks/Python.framework/Versions/3.6'
  #New python executable in /Users/karthikc/Envs/hello/bin/python3.6
  #Also creating executable in /Users/karthikc/Envs/hello/bin/python
  #Installing setuptools, pip, wheel...
  #done.
  #virtualenvwrapper.user_scripts creating /Users/karthikc/Envs/hello/bin/predeactivate
  #virtualenvwrapper.user_scripts creating /Users/karthikc/Envs/hello/bin/postdeactivate
  #virtualenvwrapper.user_scripts creating /Users/karthikc/Envs/hello/bin/preactivate
  #virtualenvwrapper.user_scripts creating /Users/karthikc/Envs/hello/bin/postactivate
  #virtualenvwrapper.user_scripts creating /Users/karthikc/Envs/hello/bin/get_env_details
  #(hello) karthikc@INCQPMAC010 ~ $

  #Now we need to install some fundamental packages

  #NumPy is the fundamental package for scientific computing with Python.
  pip3 install numpy

  #We would be using Jupyter Notebooks as IDE. Requires ipython and jupyter packages to be installed. We also would be using matplotlib for plotting graphs.
  pip3 install ipython jupyter matplotlib
  ```

- References
  - [VirtualEnv Wrapper command References](https://virtualenvwrapper.readthedocs.io/en/latest/command_ref.html)