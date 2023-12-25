# tensorflow-vm
# tensorflow-vm

```
echo "# tensorflow-vm" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/alpha-wolf-jin/tensorflow-vm.git

git config --global credential.helper 'cache --timeout 72000'

git push -u origin main

git add . ; git commit -a -m "update README" ; git push -u origin main
```

# Install RHEL 9 VM

Install RHEL9.3 VM in my lab.

```
# subscription-manager repos --enable codeready-builder-for-rhel-9-$(arch)-rpms
# dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm -y
```

# Manually dowmload the install 2 rpms

Both packages are avaiable on the RedHat portal.
```
# yum localinstall python3-ruamel-yaml-0.17.21-1.el9ap.noarch.rpm python3-ruamel-yaml-clib-0.2.6-3.el9ap.x86_64.rpm
```

```
dnf install conda -y         #installs Miniconda
conda init bash              #configures Conda to our shell
exec $SHELL                  #restarts the shell to finish installation of Miniconda
```

# Install TensorFlow
First, create a Conda environment for TensorFlow:

```
# conda create --name tf python=3.9 -y
```

Then, activate the Conda environment using the following command:

```
# conda activate tf
```

Your Conda environment status is shown in the command line within parentheses like this:

```
pip install --upgrade pip
```

Finally, we can install TensorFlow from pip. We will use the CPU-only build of TensorFlow because we are not using a GPU for ML on this system.

```
# pip install tensorflow-cpu
```

To verify that Tensorflow is running properly on the CPU, run the following command, which will execute a simple Python test program:

```
python3 -c "import tensorflow as tf; print(tf.reduce_sum(tf.random.normal([1000, 1000])))" 2>/dev/null
```

The output should look like this. The numbers may differ, but it should have this format:


# Notebook Setup

In this step, you will set up a Jupyter Notebook to run your code. First, ensure that your Conda environment is activated. When activated, your command prompt will look like this:

If it is inactive, you can activate it with the following command:

```
# conda activate tf
```

Next, install the necessary components to run the Jupyter Notebook and perform data visualization

```
# pip install notebook matplotlib
```

Finally, start the Jupyter Notebook by running the following command:

```
# mkdir -p /root/tensorflow
# nohup conda run -n tf jupyter notebook --ip=* --no-browser --allow-root -NotebookApp.password='redhat' -NotebookApp.token='redhat' --notebook-dir="/root/tensorflow" </dev/null >/dev/null 2>&1 &
```
