---
title: Chyba kompilátoru prostředků RW2001
ms.date: 11/04/2016
f1_keywords:
- RW2001
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
ms.openlocfilehash: 900bfed9d57af0f6f5dd8fac19380bb7c382addc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190739"
---
# <a name="resource-compiler-error-rw2001"></a>Chyba kompilátoru prostředků RW2001

Neplatná direktiva v předzpracovaném souboru RC

Soubor RC obsahuje direktivu **#pragma** .

Použijte direktivu preprocesoru **#ifndef** s konstantou **RC_INVOKED** , kterou kompilátor prostředků definuje při zpracovávání souboru include. Umístit direktivu **#pragma** dovnitř bloku kódu, který není zpracován při definování **RC_INVOKED** konstanty. Kód v bloku je zpracován pouze kompilátorem C/C++ a nikoli kompilátorem prostředků. Následující vzorový kód demonstruje tuto techniku:

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

Direktiva preprocesoru **#pragma** nemá žádný význam v. Soubor RC Direktiva preprocesoru **#include** se často používá v. Soubor RC, který obsahuje hlavičkový soubor (buď vlastní hlavičkový soubor založený na projektu nebo standardní hlavičkový soubor poskytnutý Microsoftem s jedním z jeho produktů). Některé z těchto vložených souborů obsahují direktivu **#pragma** . Vzhledem k tomu, že hlavičkový soubor může obsahovat jeden nebo více dalších souborů hlaviček, soubor, který obsahuje problematickou **#pragma** direktivu, nemusí být okamžitě zjevný.

Technika **#ifndef RC_INVOKED** může řídit zahrnutí hlavičkových souborů do hlavičkových souborů založených na projektu.
