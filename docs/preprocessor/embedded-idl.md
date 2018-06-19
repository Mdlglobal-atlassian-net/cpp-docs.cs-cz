---
title: embedded_idl – | Microsoft Docs
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
ms.openlocfilehash: 1e0b594952e8e5be0a9be9c843877c8c4bb95eca
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842713"
---
# <a name="embeddedidl"></a>embedded_idl
**Konkrétní C++**  
  
 Určuje, že knihovny typů je zapsán do souboru .tlh kódem generované atribut zachovaná.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
embedded_idl[("param")]  
```  
  
#### <a name="parameters"></a>Parametry  
 `param`  
 Může být jedna ze dvou hodnot:  
  
-   emitidl –: informace o typu naimportované z knihovny typelib bude k dispozici v IDL vygenerované s atributy projektu.  Toto je výchozí nastavení a bude platit, a pokud nezadáte parametr, který se `embedded_idl`.  
  
-   no_emitidl: informace o typu naimportované z knihovny typelib nebude přítomný v IDL vygenerované s atributy projektu.  
  
## <a name="example"></a>Příklad  
  
```  
// import_embedded_idl.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib2")];  
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")  
```  
  
## <a name="remarks"></a>Poznámky  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)