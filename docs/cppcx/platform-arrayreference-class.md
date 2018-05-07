---
title: Třída Platform::ArrayReference | Microsoft Docs
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c8e4183c400cf45a23f24a98292b68f6df537da1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="platformarrayreference-class"></a>Platform::ArrayReference – třída
`ArrayReference` je typ optimalizace, které může nahradit pro [Platform::Array ^](../cppcx/platform-array-class.md) ve vstupní parametry, když vyplníte pole stylu jazyka C s vloženými daty.  
  
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
|[ArrayReference::operator() – operátor](#operator-call)|Převede tento `ArrayReference` k `Platform::Array<T>^*`.|  
|[ArrayReference::operator = – operátor](#operator-assign)|Přiřadí obsah jiného `ArrayReference` k této instanci.|  
  
## <a name="exceptions"></a>Výjimky  
  
### <a name="remarks"></a>Poznámky  
 Pomocí `ArrayReference` k vyplnění pole ve stylu jazyka, vyhnete se navíc kopírování, která by být součástí kopírování nejprve do `Platform::Array` proměnnou a pak do pole ve stylu jazyka. Při použití `ArrayReference`, existuje pouze jedna kopie operace. Příklad kódu, najdete v části [pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Záhlaví:** vccorlib.h  
  
## <a name="ctor"></a>  ArrayReference::ArrayReference – konstruktor
Inicializuje novou instanci třídy [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) třídy.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);  
ArrayReference(ArrayReference&& otherArg)  
  
```  
  
### <a name="parameters"></a>Parametry  
 `dataArg`  
 Ukazatel na pole data.  
  
 `sizeArg`  
 Počet elementů ve zdrojové pole.  
  
 `otherArg`  
 `ArrayReference` Objekt, jehož data přesunou k inicializaci nové instance.  
  
### <a name="remarks"></a>Poznámky  
  


## <a name="operator-assign"></a>  ArrayReference::operator = – operátor
Zadaný objekt přiřadí aktuální [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) objekt pomocí sémantiky přesunutí.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
ArrayReference& operator=(ArrayReference&& otherArg);  
  
```  
  
### <a name="parameters"></a>Parametry  
 `otherArg`  
 Objekt, který je přesunuta do aktuální `ArrayReference` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na objekt typu `ArrayReference`.  
  
### <a name="remarks"></a>Poznámky  
 `Platform::ArrayReference` je standardní šablona C++ třídy, ne třídu ref.  
  


## <a name="operator-call"></a>  ArrayReference::operator() – operátor
Převede aktuální [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) zpět do objektu [Platform::Array](../cppcx/platform-array-class.md) třídy.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
Array<TArg>^ operator ();  
  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Na objekt popisovače typu `Array<TArg>^`  
  
### <a name="remarks"></a>Poznámky  
 [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) a [Platform::Array](../cppcx/platform-array-class.md) jsou šablony třídy standard C++, není ref třídy.  
  


  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)