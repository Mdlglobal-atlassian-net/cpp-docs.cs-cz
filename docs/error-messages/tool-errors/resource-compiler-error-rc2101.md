---
title: Chyba kompilátoru prostředků RC2101 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2101
dev_langs:
- C++
helpviewer_keywords:
- RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 196806e6d2767c889ae96d239af69113c542ba6c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034756"
---
# <a name="resource-compiler-error-rc2101"></a>Chyba kompilátoru prostředků RC2101

Neplatná direktiva v Předzpracovaný soubor RC

Obsahuje soubor Resource Compiler **#pragma** směrnice.

Použití **#ifndef** direktivy preprocesoru s konstantou RC_INVOKED, že kompilátor prostředků definuje při zpracování vloženého souboru. Místo **#pragma** direktivy uvnitř bloku kódu, který není zpracována, když je definována konstanta RC_INVOKED. Kód v bloku, jsou zpracovávána pouze kompilátor C/C++ a ne kompilátor prostředků. Následující ukázkový kód demonstruje tento postup:

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

**#Pragma** direktivy preprocesoru nemá žádný význam. Soubor RC. **#Include** direktivy preprocesoru se používá v. Soubor RC zahrnout soubor hlaviček (soubor projektu na základě vlastní hlavičky nebo standardní hlavičku souboru poskytovaných microsoftem s některou z jejích produktů). Některé z nich zahrnují soubory obsahují **#pragma** směrnice. Protože soubor hlaviček může zahrnovat jeden nebo více další hlavičkové soubory, soubor, který obsahuje je problematický **#pragma** – direktiva nemusí být hned zjevné.

**#Ifndef** včetně hlavičkové soubory v souborech hlaviček na základě projektu můžete řídit RC_INVOKED technika.