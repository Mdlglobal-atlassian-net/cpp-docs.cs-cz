---
title: Upozornění linkerů LNK4247
ms.date: 11/04/2016
f1_keywords:
- LNK4247
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
ms.openlocfilehash: 344c219fa1f3daa1e5f9c31431e608f5e7036400
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991152"
---
# <a name="linker-tools-warning-lnk4247"></a>Upozornění linkerů LNK4247

vstupní bod ' decorated_function_name ' již má atribut vlákna; atribut Attribute se ignoruje.

Vstupní bod zadaný pomocí [/entry (symbol vstupního bodu)](../../build/reference/entry-entry-point-symbol.md)má atribut Threading, ale také byl zadán parametr [/CLRTHREADATTRIBUTE (nastavit atribut vlákna CLR)](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md) s jiným modelem vláken.

Linker ignoroval hodnotu zadanou pomocí/CLRTHREADATTRIBUTE.

Řešení tohoto upozornění:

- Odeberte/CLRTHREADATTRIBUTE ze svého sestavení.

- Odeberte atribut ze souboru zdrojového kódu.

- Odeberte oba atributy ze zdroje i/CLRTHREADATTRIBUTE ze svého sestavení a přijměte výchozí model vláken CLR.

- Změňte hodnotu předanou na/CLRTHREADATTRIBUTE, například to, že souhlasí s atributem ve zdroji.

- Změnit atribut ve zdroji, například, souhlasí s hodnotou předanou do/CLRTHREADATTRIBUTE.

Následující ukázka generuje LINKERŮ LNK4247

```cpp
// LNK4247.cpp
// compile with: /clr /c
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console
[System::MTAThreadAttribute]
void functionTitle (){}
```
