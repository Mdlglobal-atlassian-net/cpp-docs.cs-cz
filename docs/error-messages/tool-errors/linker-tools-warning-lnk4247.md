---
title: Upozornění linkerů LNK4247
ms.date: 11/04/2016
f1_keywords:
- LNK4247
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
ms.openlocfilehash: cd4108f8bd06ec7a0b2d2eb9fab13917174b797b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516022"
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