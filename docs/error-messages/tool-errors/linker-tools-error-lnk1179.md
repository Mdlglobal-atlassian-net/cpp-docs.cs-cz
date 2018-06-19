---
title: Chyba linkerů Lnk1179 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1179
dev_langs:
- C++
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72a531397c3c101fbff937f293f772c5f6778523
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300212"
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