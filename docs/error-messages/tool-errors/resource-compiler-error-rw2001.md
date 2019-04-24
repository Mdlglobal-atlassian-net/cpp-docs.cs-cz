---
title: Chyba kompilátoru prostředků RW2001
ms.date: 11/04/2016
f1_keywords:
- RW2001
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
ms.openlocfilehash: 4d298cdd9d96c55f283ce7f0e2ba04dd664941f8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226502"
---
# <a name="resource-compiler-error-rw2001"></a>Chyba kompilátoru prostředků RW2001

Neplatná direktiva v Předzpracovaný soubor RC

Soubor RC obsahuje **#pragma** směrnice.

Použití **#ifndef** direktivy preprocesoru s **RC_INVOKED** konstantní, že kompilátor prostředků definuje při zpracování vloženého souboru. Místo **#pragma** direktivy uvnitř bloku kódu, který není zpracována, když **RC_INVOKED** – konstanta je definována. Kód v bloku, jsou zpracovávána pouze kompilátor C/C++ a ne kompilátor prostředků. Následující ukázkový kód demonstruje tento postup:

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

**#Pragma** direktivy preprocesoru nemá žádný význam. Soubor RC. **#Include** direktivy preprocesoru se používá v. Soubor RC zahrnout soubor hlaviček (soubor projektu na základě vlastní hlavičky nebo standardní hlavičku souboru poskytovaných microsoftem s některou z jejích produktů). Některé z nich zahrnují soubory obsahují **#pragma** směrnice. Protože soubor hlaviček může zahrnovat jeden nebo více další hlavičkové soubory, soubor, který obsahuje je problematický **#pragma** – direktiva nemusí být hned zjevné.

**#Ifndef RC_INVOKED** včetně hlavičkové soubory v souborech hlaviček na základě projektu můžete řídit technika.