---
title: "Třída CComUnkArray | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComUnkArray
- ATLCOM/ATL::CComUnkArray
- ATLCOM/ATL::CComUnkArray::CComUnkArray
- ATLCOM/ATL::CComUnkArray::Add
- ATLCOM/ATL::CComUnkArray::begin
- ATLCOM/ATL::CComUnkArray::end
- ATLCOM/ATL::CComUnkArray::GetCookie
- ATLCOM/ATL::CComUnkArray::GetUnknown
- ATLCOM/ATL::CComUnkArray::Remove
dev_langs: C++
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 14c2b7e05ed303d8b18ae40619bc63a75f025662
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomunkarray-class"></a>CComUnkArray – třída
Tato třída ukládá **IUnknown** ukazatele a je určen k použití jako parametr, který se [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) třídy šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<unsigned int nMaxSize>
class CComUnkArray
```  
  
#### <a name="parameters"></a>Parametry  
 *nMaxSize*  
 Maximální počet **IUnknown** ukazatele, které může uchovávat v statické pole.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComUnkArray::CComUnkArray](#ccomunkarray)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComUnkArray::Add](#add)|Voláním této metody lze přidat **IUnknown** ukazatel na pole.|  
|[CComUnkArray::begin](#begin)|Vrací ukazatel na první **IUnknown** ukazatele v kolekci.|  
|[CComUnkArray::end](#end)|Vrací ukazatel na jednu za posledních **IUnknown** ukazatele v kolekci.|  
|[CComUnkArray::GetCookie](#getcookie)|Volat tuto metodu za účelem získání souboru cookie přidruženého dané **IUnknown** ukazatel.|  
|[CComUnkArray::GetUnknown](#getunknown)|Voláním této metody lze získat **IUnknown** ukazatel spojené s danou souboru cookie.|  
|[CComUnkArray::Remove](#remove)|Voláním této metody lze odebrat **IUnknown** ukazatel z pole.|  
  
## <a name="remarks"></a>Poznámky  
 **CComUnkArray** obsahuje pevný počet **IUnknown** ukazatele, každý rozhraní na připojení bodu. **CComUnkArray** lze použít jako parametr, který se [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) třídy šablony. **CComUnkArray\<1 >** je specializace šablony z **CComUnkArray** který optimalizovaná pro jedno připojení k bodu.  
  
 **CComUnkArray** metody [začít](#begin) a [end](#end) slouží k procházení všechny body připojení (například při vyvolání události).  
  
 V tématu [přidání body připojení k objektu](../../atl/adding-connection-points-to-an-object.md) informace o automatizaci vytváření připojení bodu proxy.  
  
> [!NOTE]
> **Poznámka:** třídy [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md) je používán **přidat třídu** Průvodce při vytvoření ovládacího prvku, který má spojovací body. Pokud chcete určit počet bodů připojení ručně, změňte odkaz z **CComDynamicUnkArray** k `CComUnkArray<`  *n*  `>`, kde  *n*  je počet bodů připojení vyžaduje.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="add"></a>CComUnkArray::Add  
 Voláním této metody lze přidat **IUnknown** ukazatel na pole.  
  
```
DWORD Add(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 Voláním této metody lze přidat **IUnknown** ukazatel na pole.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí souboru cookie přidruženého nově přidané ukazatele, nebo 0, pokud pole není dostatečně velký, aby se tak, aby obsahovala nové ukazatele.  
  
##  <a name="begin"></a>CComUnkArray::begin  
 Vrátí ukazatel na začátek kolekce **IUnknown** rozhraní ukazatele.  
  
```
IUnknown**
    begin();
```     
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na **IUnknown** ukazatel rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Kolekce obsahuje odkazy na rozhraní místně uložené jako **IUnknown**. Každý vložíte **IUnknown** rozhraní pro typ skutečné rozhraní a pak zavolají jejím prostřednictvím. Není nutné nejprve dotaz pro rozhraní.  
  
 Před použitím **IUnknown** rozhraní, je potřeba zkontrolovat, že není **NULL**.  
  
##  <a name="ccomunkarray"></a>CComUnkArray::CComUnkArray  
 Konstruktor  
  
```
CComUnkArray();
```  
  
### <a name="remarks"></a>Poznámky  
 Nastaví kolekci pro uložení `nMaxSize` **IUnknown** ukazatele a inicializuje ukazatele na **NULL**.  
  
##  <a name="end"></a>CComUnkArray::end  
 Vrací ukazatel na jednu za posledních **IUnknown** ukazatele v kolekci.  
  
```
IUnknown**
    end();
```     
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na **IUnknown** ukazatel rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 `CComUnkArray` Metody **začít** a **end** lze použít k prosmyčkování všech spojovací body, například při vyvolání události.  
  
 [!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]  
  
##  <a name="getcookie"></a>CComUnkArray::GetCookie  
 Volat tuto metodu za účelem získání souboru cookie přidruženého dané **IUnknown** ukazatel.  
  
```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```  
  
### <a name="parameters"></a>Parametry  
 `ppFind`  
 **IUnknown** ukazatele, pro které se vyžaduje přidružených souborů cookie.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí souboru cookie přidruženého **IUnknown** ukazatel nebo 0, pokud neexistuje odpovídající **IUnknown** ukazatel myši nachází.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je více než jednu instanci stejného **IUnknown** ukazatele, funkce vrátí hodnotu souboru cookie, který pro první.  
  
##  <a name="getunknown"></a>CComUnkArray::GetUnknown  
 Voláním této metody lze získat **IUnknown** ukazatel spojené s danou souboru cookie.  
  
```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCookie`  
 Soubor cookie, pro které přidružené **IUnknown** je vyžadován.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **IUnknown** ukazatel nebo hodnota NULL, pokud je nalezen žádný odpovídající soubor cookie.  
  
##  <a name="remove"></a>CComUnkArray::Remove  
 Voláním této metody lze odebrat **IUnknown** ukazatel z pole.  
  
```
BOOL Remove(DWORD dwCookie);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCookie`  
 Odkazování na soubor cookie **IUnknown** ukazatel na odeberou z pole.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** Pokud ukazatele je odebrána, **FALSE** jinak.  
  
## <a name="see-also"></a>Viz také  
 [CComDynamicUnkArray – třída](../../atl/reference/ccomdynamicunkarray-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
