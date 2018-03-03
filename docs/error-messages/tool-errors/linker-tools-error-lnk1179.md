---
title: "Chyba linkerů Lnk1179 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1179
dev_langs:
- C++
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 93b042e928331e369d64a45aa27f5f613ce9fc31
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1179"></a>Chyba linkerů LNK1179
Neplatný nebo poškozený soubor: duplicitní sekvence COMDAT "název souboru.  
  
 Modul objektu obsahuje dvě nebo více COMDATs se stejným názvem.  
  
 Tato chyba může být způsobeno pomocí [/H](../../build/reference/h-restrict-length-of-external-names.md), což omezuje délku externích názvů, a [/Gy](../../build/reference/gy-enable-function-level-linking.md), které balíčky funkcí v COMDATs.  
  
## <a name="example"></a>Příklad  
 V následujícím kódu `function1` a `function2` jsou identické v prvních 8 znaků. Kompilování pomocí **/Gy** a **/H8** způsobí chybu odkaz.  
  
```  
void function1(void);  
void function2(void);  
  
int main() {  
    function1();  
    function2();  
}  
  
void function1(void) {}  
void function2(void) {}  
```