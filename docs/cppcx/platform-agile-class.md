---
title: "Třída Platform::Agile | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
dev_langs: C++
helpviewer_keywords: Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 71498f2a075bed78fab2bb073e5c93c62936c29d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="platformagile-class"></a>Platform::Agile – třída
Představuje objekt, který má MashalingBehavior = Standard jako agile objekt, který výrazně snižuje se možnost runtime dělení na vlákna výjimky. `Agile<T>` Umožňuje-agilní objekt, který má volání nebo volání z stejné nebo jiné vlákno. Další informace najdete v tématu [dělení na vlákna a zařazování](../cppcx/threading-and-marshaling-c-cx.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <typename T>  
class Agile;  
```  
  
#### <a name="parameters"></a>Parametry  
 T  
 Typename – agilní třídy.  
  
### <a name="remarks"></a>Poznámky  
 Většina tříd v prostředí Windows Runtime jsou agilní. Agilní objekt můžete volat nebo volat pomocí objektu vnitroprocesovou nebo out-of-proc ve stejné nebo jiné vlákno. Pokud není objekt agilní, zabalení objektu agilní ve `Agile<T>` objekt, který je agile. Pak se `Agile<T>` objekt může být zařazen a základní-agilní objekt lze použít.  
  
 `Agile<T>` Třídy je třída nativní, standard C++ a vyžaduje `agile.h`. Reprezentuje objekt agilní a agilní objekt *kontextu*. Kontext určuje model vláken a chování zařazování agilní objektu. Operační systém používá k určení jak přeuspořádat objekt kontextu.  
  
### <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Agile::Agile](#ctor)|Inicializuje novou instanci třídy Agile.|  
|[Agilní:: ~ agilní – destruktor](#dtor)|Zničí aktuální instance třídy Agile.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Agile::Get](#get)|Vrátí popisovač objektu, která je reprezentována agilní aktuálního objektu.|  
|[Agile::GetAddressOf](#getaddressof)|Znovu inicializuje aktuální agilní objekt a vrátí adresu popisovač pro objekt typu `T`.|  
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|Vrátí adresu popisovač pro objekt představovaný agilní aktuálního objektu.|  
|[Agile::Release](#release)|Zruší aktuální objekt agilní základní objekt a kontext.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[-> Agile::Operator](#operator-arrow)|Načte popisovač pro objekt představovaný agilní aktuálního objektu.|  
|[Agile::Operator =](#operator-assign)|Zadaná hodnota přiřadí aktuální agilní objekt.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Object`  
  
 `Agile`  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Záhlaví:** agile.h  

## <a name="ctor"></a>Agile::Agile – konstruktor
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
 Typ určený parametrem typename šablony.  
  
 `object`  
 V druhé verze tohoto konstruktoru objekt použitý k inicializaci nové instance Agile. V třetím verze objektu, která se zkopírují do nové instance Agile. V Čtvrtá verze objektu, která je přesunuta do nové instance Agile.  
  
### <a name="remarks"></a>Poznámky  
 První verze součásti tento konstruktor je výchozí konstruktor. Druhá verze inicializuje nové agilní instance třídy z objektu určeného `object` parametr. Třetí verzi je konstruktor copy. Je Čtvrtá verze konstruktor move. Tento konstruktor nemůže vyvolat výjimky.  

## <a name="dtor"></a>Agilní:: ~ agilní – destruktor
Zničí aktuální instance třídy Agile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
~Agile();  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento destruktor také uvolní objekt reprezentovaný rozhraním agilní aktuální objekt.  
  
## <a name="get"></a>Agile::Get – metoda
Vrátí popisovač objektu, která je reprezentována agilní aktuálního objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
   T^ Get() const  
;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro objekt, který představuje aktuální objekt Agile.  
  
 Typ vrácené hodnoty je ve skutečnosti podmínky vnitřní typ. Pohodlný způsob pro uložení návratová hodnota je přiřadit do proměnné, která je deklarovaný s **automaticky** zadejte odvození – klíčové slovo. Například `auto x = myAgileTvariable->Get();`.  
  
## <a name="getaddressof"></a>Agile::GetAddressOf – metoda
Znovu inicializuje aktuální agilní objekt a vrátí adresu popisovač pro objekt typu `T`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
T^* GetAddressOf()   
throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ určený parametrem typename šablony.  
  
### <a name="return-value"></a>Návratová hodnota  
 Adresa popisovač pro objekt typu `T`.  
  
### <a name="remarks"></a>Poznámky  
 Tato operace uvolní aktuální reprezentace objektu typu `T`, pokud existují; znovu inicializuje objekt agilní datové členy; získá aktuální kontext vláken; a potom se vrátí adresu popisovač objektu proměnné, která může představovat agilní objekt. Chcete-li způsobit instance agilní třídy představující objekt, použijte operátor přiřazení ([Agile::operator =](#operator-assign)) přiřadit instance agilní třídy objektu.  

## <a name="getaddressofforinout"></a>Agile::GetAddressOfForInOut – metoda
Vrátí adresu popisovač pro objekt představovaný agilní aktuálního objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
T^* GetAddressOfForInOut()  throw();  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ určený parametrem typename šablony.  
  
### <a name="return-value"></a>Návratová hodnota  
 Adresa popisovač pro objekt představovaný agilní aktuálního objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tato operace získá aktuální kontext vláken a vrátí adresu popisovač pro základní objekt.  

## <a name="release"></a>Agile::Release – metoda
Zruší aktuální objekt agilní základní objekt a kontext.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
void Release() throw();  
  
```  
  
### <a name="remarks"></a>Poznámky  
 Základní objekt a kontextu aktuálního objektu agilní se zahodí, pokud existují, a pak je nastavena hodnota agilní objektu na hodnotu null.  

## <a name="operator-arrow"></a>Agile::Operator -&gt; – operátor
Načte popisovač pro objekt představovaný agilní aktuálního objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
T^ operator->()   
const throw();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro objekt představovaný agilní aktuálního objektu.  
  
 Tento operátor. ve skutečnosti vrátí interní typ podmínky. Pohodlný způsob pro uložení návratová hodnota je přiřadit do proměnné, která je deklarovaný s **automaticky** zadejte odvození – klíčové slovo.  

## <a name="operator-assign"></a>Agile::Operator = – operátor
Přiřadí aktuální agilní objekt zadaného objektu.  
  
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
 V typu zadaném pomocí šablony typename.  
  
 `object`  
 Objekt nebo popisovač pro objekt, který je zkopírovat nebo přesunout do agilní aktuálního objektu.  
  
 `lp`  
 Ukazatel rozhraní IUnknown objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro objekt typu`T`  
  
### <a name="remarks"></a>Poznámky  
 První verze součásti operátor přiřazení zkopíruje popisovač typu odkaz na aktuální agilní objekt. Druhé kopie verze odkaz na Agile zadejte aktuální agilní objektu. Třetí verzi přejde Agile zadejte aktuální agilní objekt. Čtvrtý verze přesune ukazatel na objekt COM na aktuální agilní objekt.  
  
 Operace přiřazení automaticky trvá kontextu aktuálního agilní objektu. 
       
## <a name="see-also"></a>Viz také  
 [Namespace platformy](platform-namespace-c-cx.md)