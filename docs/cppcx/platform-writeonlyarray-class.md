---
title: "Třída Platform::WriteOnlyArray | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
s.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::WriteOnlyArray::begin
- VCCORLIB/Platform::WriteOnlyArray::Data
- VCCORLIB/Platform::WriteOnlyArray::end
- VCCORLIB/Platform::WriteOnlyArray::FastPass
- VCCORLIB/Platform::WriteOnlyArray::Length
- VCCORLIB/Platform::WriteOnlyArray::set
dev_langs: C++
helpviewer_keywords: Platform::WriteOnlyArray Class
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
caps.latest.revision: "11"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 32c3fc0c59f94ca35d80ebfd4f16330517399e72
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="platformwriteonlyarray-class"></a>Platform::WriteOnlyArray – třída
Představuje jednorozměrné pole, které slouží jako vstupní parametr tehdy, když volání pro metodu k vyplnění pole.  
  
 Tato třída ref je deklarován jako soukromý v vccorlib.h; proto není vygenerované v metadatech a je pouze použití z jazyka C++. Tato třída je určena pouze pro použití jako vstupní parametr, který přijímá pole, které má přidělené volající. Není zkonstruovatelný z uživatelského kódu. Umožňuje, aby metoda C++ zapisovat přímo do tohoto pole – vzor, který se označuje jako *FillArray* vzor. Další informace najdete v tématu [pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
private ref class WriteOnlyArray<T, 1>  
```  
  
### <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
 Tyto metody mají interní usnadnění – to znamená, že jsou přístupné pouze v rámci C++ aplikace nebo součást.  
  
|Název|Popis|  
|----------|-----------------|  

|[WriteOnlyArray::begin](#begin)| Iterátor, který odkazuje na první prvek pole. |  
|[WriteOnlyArray::Data](#data)| Ukazatel na vyrovnávací paměť dat. |  
|[WriteOnlyArray::end](#end)| Iterátor, který odkazuje na jeden po posledním prvkem v poli. |  
|[WriteOnlyArray::FastPass](#fastpass)| Označuje, zda pole můžete používat FastPass mechanismus, který je označený jako transparentně provádí systému. Nepoužívejte to ve vašem kódu |  
|[WriteOnlyArray::Length](#length)| Vrátí počet prvků v poli. |  
|[WriteOnlyArray::set](#set)| Nastaví zadaný element se zadanou hodnotou. |  

  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `WriteOnlyArray`  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
 **Metadata:** Platform.winmd  
  
 **Namespace:** platformy  

## <a name="begin"></a>WriteOnlyArray::begin – metoda
Vrací ukazatel na první prvek v poli.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
T* begin() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na první prvek v poli.  
  
### <a name="remarks"></a>Poznámky  
 Tato iterator lze použít s algoritmy STL, jako `std::sort` pracovat na prvků v poli.  
  


## <a name="data"></a>Vlastnost WriteOnlyArray::Data
Ukazatel na datová vyrovnávací paměť.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property T* Data{  
   T* get() const;  
}  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nezpracovaná pole bajtů.  
  


## <a name="end"></a>WriteOnlyArray::end – metoda
Vrací ukazatel na jednu po posledním prvkem v poli.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
T* end() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel iterator k jednomu po posledním prvkem v poli.  
  
### <a name="remarks"></a>Poznámky  
 Tato iterator lze použít s algoritmy STL k provádění operací, jako `std::sort` na elementy pole.  
  


## <a name="fastpass"></a>Vlastnost WriteOnlyArray::FastPass
Určuje, zda může být provedeno vnitřní FastPass optimalizace. Není určena pro použití uživatelského kódu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property bool FastPass{  
   bool get() const;  
}  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Logická hodnota, která určuje, zda pole FastPass.  
  


## <a name="get"></a>WriteOnlyArray::get – metoda
Vrátí element v zadaném indexu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
T& get(  
   unsigned int indexArg) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `indexArg`  
  
### <a name="return-value"></a>Návratová hodnota  
  


## <a name="length"></a>Vlastnost WriteOnlyArray::Length
Vrátí počet prvků v poli přidělené volajícího.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property unsigned int Length{  
   unsigned int get() const;  
}  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet prvků v poli.  
  


## <a name="set"></a>WriteOnlyArray::set – funkce
Nastaví zadanou hodnotu na zadaný index v poli.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
T& set(  
   unsigned int indexArg,  
   T valueArg);  
```  
  
### <a name="parameters"></a>Parametry  
 `indexArg`  
 Index elementu, který chcete nastavit.  
  
 `valueArg`  
 Hodnota k nastavení v `indexArg`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na element, který byl právě nastavili.  
  

  
### <a name="remarks"></a>Poznámky  
 Další informace o tom, jak interpretovat hodnota HRESULT najdete v tématu [struktura kódy chyb COM](http://go.microsoft.com/fwlink/p/?LinkId=262045).  
  
  
## <a name="see-also"></a>Viz také  
 [Namespace platformy](platform-namespace-c-cx.md)   
 [Vytváření Windows Runtime komponent v jazyce C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md)