---
title: Cdefaultchartraits – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
dev_langs:
- C++
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e591bc8c77e2130548e65c6197f9e550efc480fb
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881851"
---
# <a name="cdefaultchartraits-class"></a>Cdefaultchartraits – třída
Tato třída poskytuje dvě statické funkce pro převod znaků mezi velkými a malými písmeny.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T>  
class CDefaultCharTraits
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Typ dat uložených v kolekci.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDefaultCharTraits::CharToLower](#chartolower)|(Statické) Voláním této funkce k převedení znaku na velká písmena.|  
|[CDefaultCharTraits::CharToUpper](#chartoupper)|(Statické) Voláním této funkce k převedení znaku na malá písmena.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje funkce, které se používají ve třídě [cstringelementtraitsi –](../../atl/reference/cstringelementtraitsi-class.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="chartolower"></a>  CDefaultCharTraits::CharToLower  
 Voláním této funkce k převedení znaku na malá písmena.  
  
```
static wchar_t CharToLower(wchar_t x);  
static char CharToLower(char x);
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Znak pro převod na malá písmena.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]  
  
##  <a name="chartoupper"></a>  CDefaultCharTraits::CharToUpper  
 Voláním této funkce k převedení znaku na velká písmena.  
  
```
static wchar_t CharToUpper(wchar_t x);  
static char CharToUpper(char x);
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Znak pro převod na velká písmena.  
  
## <a name="see-also"></a>Viz také  
 [Přehled tříd](../../atl/atl-class-overview.md)
