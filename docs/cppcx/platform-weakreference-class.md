---
title: "Třída Platform::WeakReference | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Platform::WeakReference
ms.assetid: 8cfe1977-a8c7-4b7b-b539-25c77ed4c5f1
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: c161bf901b0e055885858d8570925f58e2eb971a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="platformweakreference-class"></a>Platform::WeakReference – třída
Představuje slabé odkaz na instanci třídy ref.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp 
class WeakReference  
```  
  
#### <a name="parameters"></a>Parametry  
  
### <a name="members"></a>Členové  
  
### <a name="constructors"></a>Konstruktory  
  
|Člen|Popis|  
|------------|-----------------|  
|[Weakreference::weakreference –](#ctor)|Inicializuje novou instanci třídy WeakReference.|  
  
### <a name="methods"></a>Metody  
  
|Člen|Popis|  
|------------|-----------------|  
|[Weakreference::Resolve –](#resolve)|Vrátí popisovač základní třídu ref nebo nullptr, pokud objekt již existuje.|  
  
### <a name="operators"></a>Operátory  
  
|Člen|Popis|  
|------------|-----------------|  
|[WeakReference::operator =](#operator-assign)|Objekt WeakReference přiřadí novou hodnotu.|  
|[WeakReference::operator BoolType](#booltype)|Implementuje vzor bezpečné bool.|  
  
### <a name="remarks"></a>Poznámky  
 Vlastní třídy WeakReference není třída ref a proto nedědí z Platform::Object ^ a nelze jej použít v podpis veřejná metoda.  

## <a name="operator-assign"></a>WeakReference::operator =
Přiřadí hodnotu WeakReference.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
WeakReference& operator=(decltype(__nullptr));    
WeakReference& operator=(const WeakReference& otherArg);   
WeakReference& operator=(WeakReference&& otherArg);    
WeakReference& operator=(const volatile ::Platform::Object^ const otherArg); 
```  
  
### <a name="remarks"></a>Poznámky  
 Poslední přetížení v seznamu výš umožňuje přiřadit třídu ref WeakReference proměnné. V takovém případě je přetypování dolů k třídě ref [Platform::Object](../cppcx/platform-object-class.md)^. Později obnovit původní typ zadáním jako argument pro parametr typu ve [weakreference::Resolve –\<T >](#resolve) – členská funkce.  
  
## <a name="booltype"></a>WeakReference::operator BoolType
Implementuje vzor bezpečné bool pro WeakReference – třída. Nechcete být explicitně volána z vašeho kódu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
BoolType BoolType()  
```  

## <a name="resolve"></a>Weakreference::Resolve – metoda (obor názvů Platform)
Vrátí popisovač k třídě původní ref nebo `nullptr` Pokud objekt již existuje.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
template<typename T>  
T^ Resolve() const  
```  
  
### <a name="parameters"></a>Parametry  
  
### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 Popisovač pro třídu ref, který byl dříve přidružený objekt WeakReference nebo nullptr.  
  
### <a name="example"></a>Příklad  
 Toto je volitelný popis příkladu kódu.  
  
```  
  
Bar^ bar = ref new Bar();  
//use bar...  
  
if (bar != nullptr)  
{  
    WeakReference wr(bar);  
    Bar^ newReference = wr.Resolve<Bar>();  
}  
```  
  
 Upozorňujeme, že parametr typu je T, není T ^.  
  
 
## <a name="ctor"></a>Weakreference::weakreference – konstruktor
Poskytuje různé způsoby, jak vytvořit WeakReference.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
WeakReference();  
WeakReference(decltype(__nullptr));  
WeakReference(const WeakReference& otherArg);  
WeakReference(WeakReference&& otherArg);  
explicit WeakReference(const volatile ::Platform::Object^ const otherArg);  
```  
### <a name="example"></a>Příklad  
  
```cpp    
MyClass^ mc = ref new MyClass();  
WeakReference wr(mc);  
MyClass^ copy2 = wr.Resolve<MyClass>();    
```  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)