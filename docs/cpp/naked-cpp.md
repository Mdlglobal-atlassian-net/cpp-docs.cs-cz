---
title: holé (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- naked_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84e172c24bbb87f9243a4c0de25a98c90e043acc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="naked-c"></a>naked (C++)
**Konkrétní Microsoft**  
  
 Pro funkce deklarovat s `naked` atribut, kompilátor generuje kód bez prolog a epilog kódu. Tuto funkci lze použít pro psaní vlastních sekvencí kódu epilogu nebo prologu pomocí vloženého kódu assembleru. Neviditelné funkce jsou zvláště užitečné při psaní ovladačů virtuálních zařízení.  Všimněte si, že `naked` atribut je platné jenom pro x86 a ARM a není k dispozici na [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__declspec(naked) declarator  
```  
  
## <a name="remarks"></a>Poznámky  
 Protože `naked` atribut je pouze relevantní pro definici funkce a není modifikátor typu, holé funkce musí používat syntaxi rozšířených atributů a [__declspec](../cpp/declspec.md) – klíčové slovo.  
  

 Kompilátor nemůže generovat vložená funkce pro funkci s atributem holé i v případě, že funkce je také označené [__forceinline](inline-functions-cpp.md) – klíčové slovo.  

  
 Kompilátor vydává chybu, pokud `naked` jakoukoli jinou hodnotu než definici metody třetí je použit atribut.  
  
## <a name="examples"></a>Příklady  
 Tento kód definuje funkci s `naked` atribut:  
  
```  
__declspec( naked ) int func( formal_parameters ) {}  
```  
  
 Nebo můžete případně:  
  
```  
#define Naked __declspec( naked )  
Naked int func( formal_parameters ) {}  
```  
  
 Atribut `naked` ovlivňuje pouze povahu generování kódu kompilátoru pro sekvence prologu a epilogu funkce. Neovlivňuje kód, který je generován pro volání těchto funkcí. Navíc atribut `naked` není považován za součást typu funkce a ukazatele funkce nemohou mít atribut `naked`. Kromě toho nelze atribut `naked` použít pro definici dat. Například této ukázce kódu, vygeneruje se chyba:  
  
```  
__declspec( naked ) int i;       // Error--naked attribute not  
                                 // permitted on data declarations.  
```  
  
 Atribut `naked` je relevantní pouze pro definici funkce a nemůže být zadán v prototypu funkce. Například tuto deklaraci vygeneruje Chyba kompilátoru:  
  
```  
__declspec( naked ) int func();  // Error--naked attribute not   
                                 // permitted on function declarations  
```  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Volání holé funkce](../cpp/naked-function-calls.md)