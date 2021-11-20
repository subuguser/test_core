# test_core

#define MODULE
#include <linux/module.h>
#include <linux/init.h>
#include <linux/kernel.h>

int init_module(void){
    printk("<1> Hello,World\n");
    return 0;
}

void cleanup_module(void){
    printk("<1> Goodbye.\n");
}






3) Создаем Makefile: touch ./Makefile

obj-m += mhello.o

hello-objs := mhello.c

all:
       make -C /lib/modules/$(shell uname -r)/build/ M=$(PWD) modules

clean:
       make -C /lib/modules/$(shell uname -r)/build/ M=$(PWD) clean
4) Собираем модуль и устанавливаем его с помощью insmod.

make all
insmod path/to/module.ko
В качестве ответа приложите скриншот вывода установки модуля в dmesg.
