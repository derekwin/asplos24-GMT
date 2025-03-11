linux 6.x 且 gcc != x86_64-linux-gnu-gcc-13 时，下列步骤手动编译module

# 1. 
cd /home/liujinyao/asplos24-GMT/build/module
make clean
rm -f *.c *.h *.o *.ko 
rm -rf home

# 2.
# 复制所有需要的源文件到构建目录
cp /home/liujinyao/asplos24-GMT/module/{pci.c,list.c,ctrl.c,map.c,*.h} .

# 3. 
# 指定CC，编译模块
export CC=/usr/bin/x86_64-linux-gnu-gcc-13
make -j$(nproc)

# 4. 
sudo make load
dmesg | tail