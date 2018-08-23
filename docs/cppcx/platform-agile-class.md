---
title: Platform::agile – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
dev_langs:
- C++
helpviewer_keywords:
- Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f552327156d9fc1abe5e921f3b59b1fb4132ff3d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596599"
---
# <a name="platformagile-class"></a>Platform::agile – třída
Představuje objekt, který má MashalingBehavior = standardní jako agilní objekt, což významně snižuje pravděpodobnost pro dělení na vlákna výjimky modulu runtime. `Agile<T>` Umožňuje-agilní objekt volání nebo volat ze stejné nebo jiné vlákno. Další informace najdete v tématu [vláken a zařazování](../cppcx/threading-and-marshaling-c-cx.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <typename T>  
class Agile;  
```  
  
#### <a name="parameters"></a>Parametry  
 T  
 Název typu pro třídu agile.  
  
### <a name="remarks"></a>Poznámky  
 Většina tříd v modulu Windows Runtime jsou agile. Agilní objekt lze volat nebo volat v objektu uvnitř procesu nebo v režimu out-of-proc ve stejném nebo jiném vlákně. Pokud objekt není agile, zabalte objekt agile v `Agile<T>` objekt, který je agile. Pak bude `Agile<T>` objekt může být zařazována a lze základní objekt agile.  
  
 `Agile<T>` Třídy je třída C++ nativní, standard a vyžaduje `agile.h`. Představuje-agilní objekt a agilní objekt *kontextu*. Kontext určuje agilní objekt model vláken a zařazování chování. Operační systém používá k určení způsobu zařazení objektu kontextu.  
  
### <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Agile::Agile](#ctor)|Inicializuje novou instanci třídy Agile.|  
|[Agilní:: ~ agilní – destruktor](#dtor)|Odstraní aktuální instanci třídy Agile.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Agile::Get](#get)|Vrátí popisovač pro objekt, který představuje aktuální objekt Agile.|  
|[Agile::GetAddressOf](#getaddressof)|Znovu inicializuje aktuální objekt agilní a vrátí adresu popisovač pro objekt typu `T`.|  
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|Vrátí adresu popisovač pro objekt reprezentovaný objektem aktuální Agile.|  
|[Agile::Release](#release)|Zahodí aktuální objekt agilní základní objekt a kontext.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[Agile::Operator ->](#operator-arrow)|Načte popisovač pro objekt reprezentovaný objektem aktuální Agile.|  
|[Agile::Operator =](#operator-assign)|Zadaná hodnota přiřadí aktuální objekt Agile.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Object`  
  
 `Agile`  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serverem:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Záhlaví:** agile.h  

## <a name="ctor"></a>  Agile::Agile konstruktor
Inicializuje novou instanci třídy Agile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
 Agile();  
  
Agile(T^ object);   
  
Agile(const Agile<T>& object);  
  
Agile(Agile<T>&& object);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ určený název typu parametru šablony.  
  
 `object`  
 V druhé verze tohoto konstruktoru objekt použitý k inicializaci nové instance Agile. Ve třetí verzi objektu, který se zkopíruje do nového Agilního instance. Ve čtvrtém verze objektu, který se přesune do nové instance Agile.  
  
### <a name="remarks"></a>Poznámky  
 První verze tento konstruktor je výchozí konstruktor. Druhá verze inicializuje nové agilní instance třídy z objektu určeného parametrem `object` parametru. Třetí verze je kopírovací konstruktor. Čtvrtý verze je konstruktor přesunu. Tento konstruktor nelze vyvolat výjimky.  

## <a name="dtor"></a>  Agilní:: ~ agilní – destruktor
Odstraní aktuální instanci třídy Agile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
~Agile();  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento destruktor uvolní také objekt reprezentovaný objektem aktuální Agile.  
  
## <a name="get"></a>   Agile::Get – metoda
Vrátí popisovač pro objekt, který představuje aktuální objekt Agile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
   T^ Get() const  
;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro objekt, který představuje aktuální objekt Agile.  
  
 Typ vrácené hodnoty je ve skutečnosti utajované vnitřního typu. Pohodlný způsob pro uchování hodnoty vrácené je k ní přiřadit k proměnné, která je deklarována pomocí **automaticky** klíčovým slovem odvození typu. Například `auto x = myAgileTvariable->Get();`.  
  
## <a name="getaddressof"></a>  Agile::GetAddressOf – metoda
Znovu inicializuje aktuální objekt agilní a vrátí adresu popisovač pro objekt typu `T`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
T^* GetAddressOf()   
throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ určený název typu parametru šablony.  
  
### <a name="return-value"></a>Návratová hodnota  
 Adresa popisovač pro objekt typu `T`.  
  
### <a name="remarks"></a>Poznámky  
 Tato operace uvolní aktuální reprezentace objektu typu `T`, pokud existují; znovu inicializuje agilní objekt datové členy; získá aktuální kontext dělení na vlákna; a potom vrátí adresu proměnné popisovač objektu, který může představovat agilní objektu. Chcete-li způsobit, že instance třídy Agile pro reprezentaci objektu, použijte operátor přiřazení ([Agile::operator =](#operator-assign)) přiřazení objektu k instanci třídy Agile.  

## <a name="getaddressofforinout"></a>  Agile::GetAddressOfForInOut – metoda
Vrátí adresu popisovač pro objekt reprezentovaný objektem aktuální Agile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
T^* GetAddressOfForInOut()  throw();  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ určený název typu parametru šablony.  
  
### <a name="return-value"></a>Návratová hodnota  
 Adresa popisovač pro objekt reprezentovaný objektem aktuální Agile.  
  
### <a name="remarks"></a>Poznámky  
 Tato operace získá aktuální kontext dělení na vlákna a vrátí adresu popisovač do základního objektu.  

## <a name="release"></a>  Agile::Release – metoda
Zahodí aktuální objekt agilní základní objekt a kontext.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
void Release() throw();  
  
```  
  
### <a name="remarks"></a>Poznámky  
 Základní objekt a kontext aktuálního objektu Agile se zahodí, pokud existují, a nastavte hodnotu agilní objektu na hodnotu null.  

## <a name="operator-arrow"></a>  Agile::Operator -&gt; – operátor
Načte popisovač pro objekt reprezentovaný objektem aktuální Agile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
T^ operator->()   
const throw();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro objekt reprezentovaný objektem aktuální Agile.  
  
 Tento operátor ve skutečnosti vrátí utajované vnitřního typu. Pohodlný způsob pro uchování hodnoty vrácené je k ní přiřadit k proměnné, která je deklarována pomocí **automaticky** klíčovým slovem odvození typu.  

## <a name="operator-assign"></a>  Agile::Operator = – operátor
Aktuální objekt Agile přiřadí zadaný objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
   Agile<T> operator=(T^ object) throw();  
  
   Agile<T> operator=(  
      const Agile<T>& object  
) throw();  
  
   Agile<T> operator=(  
      Agile<T>&& object  
) throw();  
  
   T^ operator=(  
      IUnknown* lp  
) throw();  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ určený název typu šablony.  
  
 `object`  
 Objekt nebo popisovač pro objekt, který je zkopírovaný ani přesunutý do aktuálního objektu Agile.  
  
 `lp`  
 Ukazatel na rozhraní IUnknown objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro objekt typu `T`  
  
### <a name="remarks"></a>Poznámky  
 První verze operátoru přiřazení zkopíruje popisovač na typ odkazu na aktuální objekt Agile. Druhé kopie verze zadejte odkaz na Agile na aktuální objekt Agile. Třetí verze přejde Agile zadejte aktuální objekt Agile. Čtvrtý verze přesune ukazatel myši na objekt modelu COM s aktuálním objektem Agile.  
  
 Operace přiřazení automaticky opakuje kontextu aktuálního objektu Agile. 
       
## <a name="see-also"></a>Viz také  
 [Platforma Namespace](platform-namespace-c-cx.md)