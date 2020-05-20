---
layout: post
title: Openstack vs RHV
subtitle: Diferencias entre Openstack vs RHV
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [OpenStack]
comments: true



Red Hat Virtualization – Virtual Datacenter
Re Hat OpenStack – IaaS

En terminaos generales, ambos productos cuentan con la misma finalidad, crear maquinas virtuales/instancias de sistema operativos utilizando ciertos recursos de computo (IaaS /
PaaS) como se puede visualizar en el siguiente gráfico presentado por Red Hat donde ubican los dos productos sobre la misma linea base dentro de su infraestructura de Cloud

Ambos productos cuentan con sus proyectos Upstream o libres:
Red Hat Virutalizacion – oVirt
Red Hat Enterprise Linux Openstack Platform – OpenStack RDO

Ambas soluciones ofrecen la posibilidad de cara al cliente final brinda el servicio de Infraestructura como Servicio, ya que el cliente finalmente lo que obtiene es una instancia de
sistema operativo sobre la cual instalara sus productos, las diferencias radican en los siguientes aspectos:

Para tener un panorama comparativo a gran escala, se puede visualizar Openstack con la forma como Amazon, Azure, Google Cloud, Rackspace, entre otros ofrecen sus servicios de nube, esto
va ligado a una serie de desarrollos propios de cada fabricante para integrar la plataforma con un portal de auto aprovisionamiento y gestión de pagos, Openstack aunque esta pensada como una solución de Cloud Híbrida, las instancias o maquinas virtuales
generalmente son creadas a partir de un sistema operativo base y a partir de este se inicia la instalación de cada producto, por lo que realizar migraciones de sistemas operativos en
funcionamiento no esta dentro de sus objetivos principales, En cuanto a RHV/Ovirt, se puede visualizar como una solución de datacenter virtual, que permite la consolidación de servicios internos y la publicación de servicios externos en una plataforma
de virtualizacion robusta administrada completamente desde una interfase web, las maquinas virtuales que se inician se pueden crear desde cero a partir de un ISO de instalación o a partir de una plantilla de sistema operativos

Algunos características en las que se diferencian ambos productos son:

##Maquinas virtuales / Instancias

|RHV/ Ovirt| Red Hat OpenStack / RDO  |
|--|--|
| Desde la interfase Web, el usuario puede realizar la instalación del sistema operativo desde cero, a partir de una imagen de Sistema Operativo y/o a partir de una plantilla y/o importando una maquina virtual previamente creada | Desde la interfase Web, el usuario lanza un sistema operativo previamente creado, Openstack no permite la instalación de sistemas operativos nuevos, únicamente lanzar instancias desde imágenes (previamente creadas en infraestructuras diferentes). |
|Las maquinas virtuales pueden ser importadas y exportadas fácilmente| Las maquinas virtuales pueden ser exportadas si se instala un modulo/producto adicional de almacenamiento de imágenes |
|Las maquinas virtuales pueden residir en soluciones de almacenamiento tradicional como NFS, iSCSI, FC y en soluciones de tipo SDS (Software-defined storage )|La arquitectura de computo esta pensada para uso de soluciones de almacenamiento no tradicionales (lo ideal es almacenar la información en soluciones de tipo SDS Software-defined storage )


##Interfase administración Web

|RHV/ Ovirt| Red Hat OpenStack / RDO  |
|--|--|
| Cuenta con una interfase web que permite la creación y administración de maquinas virtuales basada en usuarios y en roles |Cuenta con una interfase web que permite la creación y administración de instancias / maquinas virtuales basada en proyectos
|Cuenta con portal de usuarios en caso que que desee utilizar como una solución de VDI (virtual desktop infrastructure)|Su interfase web es única, el usuario de proyecto define si quiere crear un servidor o un desktop |
|Permite definir roles de usuario de forma granular para definir los accesos a la infraestructura |Un usuario debe pertenecer a un proyecto, el cual tiene una cuota de uso, lo que le permite utilizar solo lo que se compro / pago|
|Genera reportes de uso de la infraestructura por usuario, maquina virtual y recursos usados a través de la herramienta Jasper Reports|Genera reportes de uso de la infraestructura por proyecto y recursos asociados a la quota del proyecto y los almacena en Base de datos|
|Su interfase Web esta pensada para la administración de recursos virtuales administrados por personal interno de datacenter|Su interfase Web esta pensada como un portal para administración de recursos virtuales administrados por cualquier usuario|



##Administración

|RHV/ Ovirt| Red Hat OpenStack / RDO  |
|--|--|
|Ovirt es un proyecto de virtualizacion para la gestión de recursos virtuales de forma tradicional, para su administración se requieren conocimientos en gestión de maquinas virtuales y soluciones de almacenamiento tradicionales | Openstack es un proyecto de gestión de recursos virtuales pensado para las empresas que buscan ofrecer nube publica (Amazon/Azure), desde el punto de vista administrativo se requieren conocimientos en los diferentes proyectos que lo componen como nova (computo) neutron (redes) glance (imágenes) cinder (almacenamiento) ceilometer (métricas) horizon (portal/dashboard) y el proyecto ceph para almacenamiento de tipo SDS |


##Crecimiento

|RHV/ Ovirt| Red Hat OpenStack / RDO  |
|--|--|
| Permite el crecimiento horizontal y vertical adicionando mas recursos a los hipervisores o simplemente adicionando mas equipos como hipervisores al pool de recursos | Esta pensado para el crecimiento horizontal, adicionando mas hipervisores y recursos a la infraestructura |
|A nivel de almacenamiento el crecimiento es vertical adicionando mas discos u otras solución de almacenamiento |A nivel de almacenamiento, el crecimiento esta pensado de forma horizontal, con soluciones como ceph, el cual permite usar métodos de almacenamiento por software|
|El backup se puede realizar con los métodos tradicionales, ya que se puede hacer backup a la solucione de almacenamiento o exportar la maquina virtual|Se debe contar con una solución compatible con almacenamiento por software o generar una estrategia de backup a travez de scripts|
||Openstack se puede integrar con soluciones de virtualizacion como ovirt/RHEV, Vmware- vCenter y HyperV
|
