---
title: Upozornění Linkerů LNK4247 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4247
dev_langs:
- C++
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d84a5964cb8df5d2973b6031da55d48dade584e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078007"
---
# <a name="linker-tools-warning-lnk4247"></a>Upozornění linkerů LNK4247

atribut vlákna; již obsahuje vstupní bod "decorated_function_name. ignoruje atribut

Vstupní bod, zadaný [/Entry (Symbol vstupního bodu)](../../build/reference/entry-entry-point-symbol.md), měl atribut dělení na vlákna, ale [/CLRTHREADATTRIBUTE (nastavit atribut modulu CLR vlákno)](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md) byl taky zadaný s jinou model vláken.

Propojovací program ignoruje hodnotu zadanou pomocí /CLRTHREADATTRIBUTE.

Chcete-li vyřešit tato upozornění:

- Odeberte /CLRTHREADATTRIBUTE z vašeho sestavení.

- Odeberte atribut ze souboru zdrojového kódu.

- Odeberte obě atribut ze zdroje a /CLRTHREADATTRIBUTE z vašeho sestavení a přijměte výchozí model dělení na vlákna modulu CLR.

- Hodnota předaná /CLRTHREADATTRIBUTE, změňte tak, že souhlasí s atributem ve zdroji.

- Změňte atribut ve zdroji, tak, že souhlasí s hodnotu předanou /CLRTHREADATTRIBUTE.

Následující ukázka generuje LNK4247

```
// LNK4247.cpp
// compile with: /clr /c
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console
[System::MTAThreadAttribute]
void functionTitle (){}
```