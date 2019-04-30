---
title: Chyba kompilátoru prostředků RC2101
ms.date: 11/04/2016
f1_keywords:
- RC2101
helpviewer_keywords:
- RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
ms.openlocfilehash: 595e87b73d79a01993e0e9b3aaa814332b21413f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345276"
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