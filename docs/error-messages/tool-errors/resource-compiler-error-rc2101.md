---
title: Chyba kompilátoru prostředků RC2101
ms.date: 11/04/2016
f1_keywords:
- RC2101
helpviewer_keywords:
- RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
ms.openlocfilehash: 3fb576758e447c54e4ddfe7ddb024a1fd35a65f2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191649"
---
# <a name="resource-compiler-error-rc2101"></a>Chyba kompilátoru prostředků RC2101

Neplatná direktiva v předzpracovaném souboru RC

Soubor kompilátoru prostředků obsahuje direktivu **#pragma** .

Použijte direktivu preprocesoru **#ifndef** s konstantou RC_INVOKED, kterou kompilátor prostředků definuje při zpracovávání souboru include. Umístit direktivu **#pragma** dovnitř bloku kódu, který není zpracován při definování RC_INVOKED konstanty. Kód v bloku je zpracován pouze kompilátorem C/C++ a nikoli kompilátorem prostředků. Následující vzorový kód demonstruje tuto techniku:

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

Direktiva preprocesoru **#pragma** nemá žádný význam v. Soubor RC Direktiva preprocesoru **#include** se často používá v. Soubor RC, který obsahuje hlavičkový soubor (buď vlastní hlavičkový soubor založený na projektu nebo standardní hlavičkový soubor poskytnutý Microsoftem s jedním z jeho produktů). Některé z těchto vložených souborů obsahují direktivu **#pragma** . Vzhledem k tomu, že hlavičkový soubor může obsahovat jeden nebo více dalších souborů hlaviček, soubor, který obsahuje problematickou **#pragma** direktivu, nemusí být okamžitě zjevný.

Technika **#ifndef** RC_INVOKED může řídit zahrnutí hlavičkových souborů do hlavičkových souborů založených na projektu.
