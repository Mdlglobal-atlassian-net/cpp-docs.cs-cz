---
title: embedded_idl | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- embedded_idl
dev_langs:
- C++
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b41af8375249a48ac3a866af224370b19f071d28
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465204"
---
# <a name="embeddedidl"></a>embedded_idl
**Specifické pro C++**  
  
Určuje, že knihovna typů je zapsána do souboru .tlh se zachovaným kódem atributem generován.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
embedded_idl[("param")]  
```  
  
### <a name="parameters"></a>Parametry  
*Param*  
Může být jedna ze dvou hodnot:  
  
- emitidl: informace o typu naimportované z knihovny typelib bude k dispozici v generované projektu s atributy IDL.  Toto je výchozí nastavení a bude platit, pokud nezadáte parametr `embedded_idl`.  
  
- no_emitidl: informace o typu naimportované z knihovny typelib nemusí být v generované projektu s atributy IDL.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// import_embedded_idl.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib2")];  
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")  
```  
  
## <a name="remarks"></a>Poznámky  
 
**Specifické pro END C++**  
  
## <a name="see-also"></a>Viz také  
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)