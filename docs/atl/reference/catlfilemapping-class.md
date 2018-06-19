---
title: Třída CAtlFileMapping | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 524e5d9c7cef5bcff0d72ddf1225ef79b1b26d64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358833"
---
# <a name="catlfilemapping-class"></a>CAtlFileMapping – třída
Tato třída reprezentuje soubor mapované paměti, operátor přetypování přidávání do metod třídy [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T = char>  
class CAtlFileMapping : public CAtlFileMappingBase
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ dat používat pro operátor přetypování.  
  
## <a name="members"></a>Členové  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlFileMapping::operator T *](#operator_t_star)|Umožňuje implicitní převod `CAtlFileMapping` objekty ke `T` **\***.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída přidává operátor přetypování jedné umožňuje implicitní převod `CAtlFileMapping` objekty ke `T` **\***. Jiní členové jsou zadaná v základní třídě [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)  
  
 `CAtlFileMapping`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlfile.h  
  
##  <a name="operator_t_star"></a>  CAtlFileMapping::operator T *  
 Umožňuje implicitní převod `CAtlFileMapping` objekty ke `T` **\***.  
  
```  
operator T*() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `T` **\*** ukazatel na začátek souboru mapované paměti.  
  
### <a name="remarks"></a>Poznámky  
 Volání [CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) a reinterprets Vrácený ukazatel jako `T` **\*** kde *T* je typ použít jako šablonu parametr této třídy.  
  
## <a name="see-also"></a>Viz také  
 [CAtlFileMappingBase – třída](../../atl/reference/catlfilemappingbase-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
