---
title: Platform::arrayreference – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
dev_langs:
- C++
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7b2a0fd8c4903852e88fa80f12bc05894625888
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42588308"
---
# <a name="platformarrayreference-class"></a>Platform::arrayreference – třída
`ArrayReference` je typ optimalizace, která může nahradit pro [Platform::Array ^](../cppcx/platform-array-class.md) ve vstupní parametry, pokud chcete vyplnit pole stylu C se vstupními daty.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class ArrayReference  
```
  
### <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[ArrayReference::ArrayReference](#ctor)|Inicializuje novou instanci třídy `ArrayReference` třídy.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[ArrayReference::operator() – operátor](#operator-call)|Převede `ArrayReference` k `Platform::Array<T>^*`.|  
|[ArrayReference::operator = – operátor](#operator-assign)|Přiřadí obsah jiného `ArrayReference` k této instanci.|  
  
## <a name="exceptions"></a>Výjimky  
  
### <a name="remarks"></a>Poznámky  
 S použitím `ArrayReference` k vyplnění pole stylu C, byste se vyhnout operaci navíc kopírování, která bude zahrnuta při prvním kopírování do `Platform::Array` proměnné a potom do pole stylu C. Při použití `ArrayReference`, existuje pouze jedna kopie operace. Příklad kódu naleznete v tématu [pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serverem:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Záhlaví:** vccorlib.h  
  
## <a name="ctor"></a>  ArrayReference::ArrayReference konstruktor
Inicializuje novou instanci třídy [Platform::arrayreference –](../cppcx/platform-arrayreference-class.md) třídy.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);  
ArrayReference(ArrayReference&& otherArg)  
  
```  
  
### <a name="parameters"></a>Parametry  
 `dataArg`  
 Ukazatel na data pole.  
  
 `sizeArg`  
 Počet elementů ve zdrojovém poli.  
  
 `otherArg`  
 `ArrayReference` Jejichž data se přesunou do inicializuje novou instanci objektu.  
  
### <a name="remarks"></a>Poznámky  
  


## <a name="operator-assign"></a>  ArrayReference::operator = – operátor
Přiřadí zadaný objekt do aktuální [Platform::arrayreference –](../cppcx/platform-arrayreference-class.md) pomocí sémantiky přesunutí objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
ArrayReference& operator=(ArrayReference&& otherArg);  
  
```  
  
### <a name="parameters"></a>Parametry  
 `otherArg`  
 Objekt, který je přesunut do aktuální `ArrayReference` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na objekt typu `ArrayReference`.  
  
### <a name="remarks"></a>Poznámky  
 `Platform::ArrayReference` je standardní C++ šablony třídy, ne ref class.  
  


## <a name="operator-call"></a>  ArrayReference::operator() – operátor
Převede aktuální [Platform::arrayreference –](../cppcx/platform-arrayreference-class.md) zpět do objektu [Platform::Array](../cppcx/platform-array-class.md) třídy.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
Array<TArg>^ operator ();  
  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Na objekt popisovače typu `Array<TArg>^`  
  
### <a name="remarks"></a>Poznámky  
 [Platform::arrayreference –](../cppcx/platform-arrayreference-class.md) a [Platform::Array](../cppcx/platform-array-class.md) jsou třídy šablony třídy standard C++, ne ref.  
  


  
  
## <a name="see-also"></a>Viz také  
 [Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)