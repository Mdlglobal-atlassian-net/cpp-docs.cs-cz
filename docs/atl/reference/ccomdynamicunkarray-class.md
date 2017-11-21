---
title: "Třída CComDynamicUnkArray | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::Add
- ATLCOM/ATL::CComDynamicUnkArray::begin
- ATLCOM/ATL::CComDynamicUnkArray::clear
- ATLCOM/ATL::CComDynamicUnkArray::end
- ATLCOM/ATL::CComDynamicUnkArray::GetAt
- ATLCOM/ATL::CComDynamicUnkArray::GetCookie
- ATLCOM/ATL::CComDynamicUnkArray::GetSize
- ATLCOM/ATL::CComDynamicUnkArray::GetUnknown
- ATLCOM/ATL::CComDynamicUnkArray::Remove
dev_langs: C++
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 51ad16bacf147e2bafc1cc2ad1a9bb835067ee40
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkArray – třída
Tato třída ukládá pole **IUnknown** ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComDynamicUnkArray
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|Konstruktor Inicializuje kolekci hodnoty tak, aby **NULL** a velikosti kolekce na nulu.|  
|[CComDynamicUnkArray:: ~ CComDynamicUnkArray](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComDynamicUnkArray::Add](#add)|Voláním této metody lze přidat `IUnknown` ukazatel na pole.|  
|[CComDynamicUnkArray::begin](#begin)|Vrací ukazatel na první `IUnknown` ukazatele v kolekci.|  
|[CComDynamicUnkArray::clear](#clear)|Vyprázdní pole.|  
|[CComDynamicUnkArray::end](#end)|Vrací ukazatel na jednu za posledních **IUnknown** ukazatele v kolekci.|  
|[CComDynamicUnkArray::GetAt](#getat)|Načte element v zadaném indexu.|  
|[CComDynamicUnkArray::GetCookie](#getcookie)|Volat tuto metodu za účelem získání souboru cookie přidruženého dané **IUnknown** ukazatel.|  
|[CComDynamicUnkArray::GetSize](#getsize)|Vrátí délku pole.|  
|[CComDynamicUnkArray::GetUnknown](#getunknown)|Voláním této metody lze získat **IUnknown** ukazatel spojené s danou souboru cookie.|  
|[CComDynamicUnkArray::Remove](#remove)|Voláním této metody lze odebrat **IUnknown** ukazatel z pole.|  
  
## <a name="remarks"></a>Poznámky  
 **CComDynamicUnkArray** obsahuje dynamicky přidělené pole **IUnknown** ukazatele, každý rozhraní na připojení bodu. **CComDynamicUnkArray** lze použít jako parametr, který se [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) třídy šablony.  
  
 **CComDynamicUnkArray** metody [začít](#begin) a [end](#end) slouží k procházení všechny body připojení (například při vyvolání události).  
  
 V tématu [přidání body připojení k objektu](../../atl/adding-connection-points-to-an-object.md) informace o automatizaci vytváření připojení bodu proxy.  
  
> [!NOTE]
> **Poznámka:** třídy **CComDynamicUnkArray** je používán **přidat třídu** Průvodce při vytvoření ovládacího prvku, který má spojovací body. Pokud chcete určit počet bodů připojení ručně, změňte odkaz z **CComDynamicUnkArray** k `CComUnkArray<`  *n*  `>`, kde  *n*  je počet bodů připojení vyžaduje.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="add"></a>CComDynamicUnkArray::Add  
 Voláním této metody lze přidat **IUnknown** ukazatel na pole.  
  
```
DWORD Add(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 **IUnknown** ukazatele pro přidání do pole.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí souboru cookie přidruženého nově přidané ukazatele.  
  
##  <a name="begin"></a>CComDynamicUnkArray::begin  
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
  
##  <a name="clear"></a>CComDynamicUnkArray::clear  
 Vyprázdní pole.  
  
```
void clear();
```  
  
##  <a name="ccomdynamicunkarray"></a>CComDynamicUnkArray::CComDynamicUnkArray  
 Konstruktor  
  
```
CComDynamicUnkArray();
```  
  
### <a name="remarks"></a>Poznámky  
 Nastaví velikost kolekce na hodnotu nula a inicializuje hodnoty tak, aby **NULL**. Destruktoru uvolní kolekce, v případě potřeby.  
  
##  <a name="dtor"></a>CComDynamicUnkArray:: ~ CComDynamicUnkArray  
 Destruktor.  
  
```
~CComDynamicUnkArray();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní prostředky přidělené pomocí konstruktoru třídy.  
  
##  <a name="end"></a>CComDynamicUnkArray::end  
 Vrací ukazatel na jednu za posledních **IUnknown** ukazatele v kolekci.  
  
```
IUnknown**
    end();
```     
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na **IUnknown** ukazatel rozhraní.  
  
##  <a name="getat"></a>CComDynamicUnkArray::GetAt  
 Načte element v zadaném indexu.  
  
```
IUnknown* GetAt(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index elementu, který chcete načíst.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) rozhraní.  
  
##  <a name="getcookie"></a>CComDynamicUnkArray::GetCookie  
 Volat tuto metodu za účelem získání souboru cookie přidruženého dané **IUnknown** ukazatel.  
  
```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```  
  
### <a name="parameters"></a>Parametry  
 `ppFind`  
 **IUnknown** ukazatele, pro které se vyžaduje přidružených souborů cookie.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí souboru cookie přidruženého **IUnknown** ukazatel nebo nula, pokud neexistuje odpovídající **IUnknown** ukazatel myši nachází.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je více než jednu instanci stejného **IUnknown** ukazatele, funkce vrátí hodnotu souboru cookie, který pro první.  
  
##  <a name="getsize"></a>CComDynamicUnkArray::GetSize  
 Vrátí délku pole.  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka pole.  
  
##  <a name="getunknown"></a>CComDynamicUnkArray::GetUnknown  
 Voláním této metody lze získat **IUnknown** ukazatel spojené s danou souboru cookie.  
  
```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCookie`  
 Soubor cookie, pro které přidružené **IUnknown** je vyžadován.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **IUnknown** ukazatel nebo hodnota NULL, pokud je nalezen žádný odpovídající soubor cookie.  
  
##  <a name="remove"></a>CComDynamicUnkArray::Remove  
 Voláním této metody lze odebrat **IUnknown** ukazatel z pole.  
  
```
BOOL Remove(DWORD dwCookie);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCookie`  
 Odkazování na soubor cookie **IUnknown** ukazatel na odeberou z pole.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud je ukazatel odebrán; jinak hodnota FALSE.  
  
## <a name="see-also"></a>Viz také  
 [CComUnkArray – třída](../../atl/reference/ccomunkarray-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
