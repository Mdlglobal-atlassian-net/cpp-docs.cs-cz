---
title: "Třída CComAutoCriticalSection | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
dev_langs: C++
helpviewer_keywords: CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 39bae0c1a5f78b852a92d10c4bb06fcb96f0e51d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection – třída
`CComAutoCriticalSection`poskytuje metody pro získání a uvolněním vlastnictví objektu kritická sekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComAutoCriticalSection : public CComCriticalSection
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|Konstruktor|  
|[CComAutoCriticalSection:: ~ CComAutoCriticalSection](#dtor)|Destruktor.|  
  
## <a name="remarks"></a>Poznámky  
 `CComAutoCriticalSection`je podobná třída [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), s výjimkou `CComAutoCriticalSection` automaticky inicializuje objekt kritická sekce v konstruktoru.  
  
 Obvykle použijete, `CComAutoCriticalSection` prostřednictvím `typedef` název [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Tento název odkazuje `CComAutoCriticalSection` při [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) je používán.  

  
 `Init` a `Term` metody z [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) nejsou k dispozici při použití této třídy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComAutoCriticalSection`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcore.h  
  
##  <a name="ccomautocriticalsection"></a>CComAutoCriticalSection::CComAutoCriticalSection  
 Konstruktor  
  
```
CComAutoCriticalSection();
```  
  
### <a name="remarks"></a>Poznámky  
 Volá funkci Win32 [InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472), který inicializuje objekt kritická sekce.  
  
##  <a name="dtor"></a>CComAutoCriticalSection:: ~ CComAutoCriticalSection  
 Destruktor.  
  
```
~CComAutoCriticalSection() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání destruktoru [DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552), což uvolní všechny prostředky systému používané objektem kritická sekce.  
  
## <a name="see-also"></a>Viz také  
 [CComFakeCriticalSection – třída](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [CComCriticalSection – třída](../../atl/reference/ccomcriticalsection-class.md)