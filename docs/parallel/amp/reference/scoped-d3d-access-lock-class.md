---
title: "scoped_d3d_access_lock – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
dev_langs:
- C++
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a592249221129bce35f8592dcec56ff2379472d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="scopedd3daccesslock-class"></a>scoped_d3d_access_lock – třída
Obálka RAII na zámek přístup D3D accelerator_view objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
class scoped_d3d_access_lock;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[scoped_d3d_access_lock Constructor](#ctor)|Přetíženo. Vytvoří `scoped_d3d_access_lock` objektu. Zámek je vydala, když se tento objekt dostane mimo rozsah.|  
|[~scoped_d3d_access_lock Destructor](#dtor)|Uvolní zámek D3D přístup přidruženého `accelerator_view` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operator=](#operator_eq)|Vlastníkem zámku z jiné `scoped_d3d_access_lock`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `scoped_d3d_access_lock`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amprt.h  
  
 **Namespace:** Concurrency::Direct3D –  

##  <a name="ctor"></a> scoped_d3d_access_lock 

 Vytvoří `scoped_d3d_access_lock` objektu. Zámek je vydala, když se tento objekt dostane mimo rozsah.  
 
```  
explicit scoped_d3d_access_lock(// [1] constructor  
    accelerator_view& _Av);

 
explicit scoped_d3d_access_lock(// [2] constructor  
    accelerator_view& _Av,  
    adopt_d3d_access_lock_t _T);

 
scoped_d3d_access_lock(// [3] move constructor  
    scoped_d3d_access_lock&& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `_Av`  
 `accelerator_view` Zámek přijmout.  
  
 `_T`  
 `adopt_d3d_access_lock_t` Objektu.  
  
 `_Other`  
 `scoped_d3d_access_lock` Objekt ze kterého chcete přesunout existující zámku.  
  
## <a name="construction"></a>Konstrukce  
 [1] – konstruktor  
 Získá zámek D3D přístup na danou [accelerator_view](accelerator-view-class.md) objektu. Vytváření bloků, dokud se získat zámek.  
  
 [2] konstruktor  
 Přijmout zámek D3D přístup z danou [accelerator_view](accelerator-view-class.md) objektu.  
  
 [3] konstruktor move  
 Přebírá přístup zámek existující D3D z jiné `scoped_d3d_access_lock` objektu. Konstrukce neblokuje.  

  
##  <a name="dtor"></a> ~scoped_d3d_access_lock 

 Uvolní zámek D3D přístup přidruženého `accelerator_view` objektu.  
  
```  
~scoped_d3d_access_lock();
```  
## <a name="operator_eq"></a> operátor = 

Vlastníkem zámek D3D přístup z jiné `scoped_d3d_access_lock` objekt, uvolnění předchozí uzamčení.  
 
```  
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 Accelerator_view, ze kterého chcete přesunout zámek D3D přístup.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `scoped_accelerator_view_lock`.  

## <a name="see-also"></a>Viz také  
 [Concurrency::direct3d – obor názvů](concurrency-direct3d-namespace.md)
