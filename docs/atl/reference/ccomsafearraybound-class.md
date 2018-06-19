---
title: Třída CComSafeArrayBound | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
dev_langs:
- C++
helpviewer_keywords:
- CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 455e71cd0ee323df8cfe43001f87179c649eefe5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364050"
---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound – třída
Tato třída je obálka pro [SAFEARRAYBOUND](http://msdn.microsoft.com/en-us/303a9bdb-71d6-4f14-8747-84cf84936c6d) struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComSafeArrayBound : public SAFEARRAYBOUND
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CComSafeArrayBound](#ccomsafearraybound)|Konstruktor|  
|[GetCount –](#getcount)|Volejte tuto metodu vrátit počet elementů.|  
|[GetLowerBound](#getlowerbound)|Volejte tuto metodu vrátit dolní hranice.|  
|[GetUpperBound](#getupperbound)|Voláním této metody vrátit horní mez.|  
|[SetCount](#setcount)|Volejte tuto metodu a nastavit počet elementů.|  
|[SetLowerBound](#setlowerbound)|Voláním této metody lze nastavit dolní mez.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](#operator_eq)|Nastaví `CComSafeArrayBound` na novou hodnotu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída je obálka pro **SAFEARRAYBOUND** struktura používané [CComSafeArray](../../atl/reference/ccomsafearray-class.md). Poskytuje metody pro dotazy a nastavení horní a dolní meze jedné dimenze `CComSafeArray` objekt a počet prvků, které obsahuje. Multidimenzionální `CComSafeArray` objektu používá pole `CComSafeArrayBound` objekty, jednu pro každou dimenzi. Proto při použití metody, jako [GetCount](#getcount), uvědomte si, že tato metoda nevrátí celkový počet elementů v multidimenzionálního pole.  
  
 **Záhlaví:** atlsafe.h  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsafe.h  
  
##  <a name="ccomsafearraybound"></a>  CComSafeArrayBound::CComSafeArrayBound  
 Konstruktor  
  
```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ulCount`  
 Počet prvků v poli.  
  
 `lLowerBound`  
 Dolní mez, ze kterého je číslované pole.  
  
### <a name="remarks"></a>Poznámky  
 Pokud pole je přístupná z programu Visual C++, doporučujeme, aby dolní hranice být definován jako 0. To může být vhodnější použít jiné dolní meze hodnotu, pokud pole se použije s jinými jazyky, jako je například jazyka Visual Basic.  
  
##  <a name="getcount"></a>  CComSafeArrayBound::GetCount  
 Volejte tuto metodu vrátit počet elementů.  
  
```
ULONG GetCount() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet prvků.  
  
### <a name="remarks"></a>Poznámky  
 Pokud přidruženého `CComSafeArray` objekt představuje multidimenzionálního pole, tato metoda vrátí jenom celkový počet elementů v dimenzi úplně vpravo. Použití [CComSafeArray::GetCount](../../atl/reference/ccomsafearray-class.md#getcount) získat celkový počet elementů.  
  
##  <a name="getlowerbound"></a>  CComSafeArrayBound::GetLowerBound  
 Volejte tuto metodu vrátit dolní hranice.  
  
```
LONG GetLowerBound() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí dolní mez `CComSafeArrayBound` objektu.  
  
##  <a name="getupperbound"></a>  CComSafeArrayBound::GetUpperBound  
 Voláním této metody vrátit horní mez.  
  
```
LONG GetUpperBound() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí horní hranice `CComSafeArrayBound` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Horní mez závisí na počtu elementy a hodnoty dolní mez. Například pokud dolní hranice je 0 a 10 je počet elementů, horní mez bude automaticky nastavit do 9.  
  
##  <a name="operator_eq"></a>  CComSafeArrayBound::operator =  
 Nastaví `CComSafeArrayBound` na novou hodnotu.  
  
```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bound`  
 A `CComSafeArrayBound` objektu.  
  
 `ulCount`  
 Počet elementů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel `CComSafeArrayBound` objektu.  
  
### <a name="remarks"></a>Poznámky  
 `CComSafeArrayBound` Objekt lze přiřadit pomocí stávající `CComSafeArrayBound`, nebo zadáním počet elementů, ve kterých případ dolní hranice ve výchozím nastavení nastavena na hodnotu 0.  
  
##  <a name="setcount"></a>  CComSafeArrayBound::SetCount  
 Volejte tuto metodu a nastavit počet elementů.  
  
```
ULONG SetCount(ULONG ulCount) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ulCount`  
 Počet elementů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet prvků v `CComSafeArrayBound` objektu.  
  
##  <a name="setlowerbound"></a>  CComSafeArrayBound::SetLowerBound  
 Voláním této metody lze nastavit dolní mez.  
  
```
LONG SetLowerBound(LONG lLowerBound) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lLowerBound`  
 Dolní mez.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí nový dolní mez `CComSafeArrayBound` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud pole je přístupná z programu Visual C++, doporučujeme, aby dolní hranice být definován jako 0. To může být vhodnější použít jiné dolní meze hodnotu, pokud pole se použije s jinými jazyky, jako je například jazyka Visual Basic.  
  
 Horní mez závisí na počtu elementy a hodnoty dolní mez. Například pokud dolní hranice je 0 a 10 je počet elementů, horní mez bude automaticky nastavit do 9.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
