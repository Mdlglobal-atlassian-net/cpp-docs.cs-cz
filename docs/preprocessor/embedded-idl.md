---
title: "embedded_idl – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: embedded_idl
dev_langs: C++
helpviewer_keywords: embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0a83b635dc7d408b6296c0407984ddfb9a9f3659
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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