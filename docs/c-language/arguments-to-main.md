---
title: Argumenty operace main
ms.date: 11/04/2016
ms.assetid: 39824fef-05ad-461d-ae82-49447dda8060
ms.openlocfilehash: 918be9d281f1cb12c27c6c2f5dd834e4af137179
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313555"
---
# <a name="arguments-to-main"></a>Argumenty operace main

**2.1.2.2.1 ANSI** Sémantika argumentů Main

V jazyce Microsoft C je funkce volána při spuštění programu označována jako **Main**. Pro **Main**není deklarován žádný prototyp a lze jej definovat s nula, dvěma nebo třemi parametry:

```
int main( void )
int main( int argc, char *argv[] )
int main( int argc, char *argv[], char *envp[] )
```

Výše uvedený třetí řádek, kde **Main** přijímá tři parametry, je rozšířením společnosti Microsoft pro standard ANSI C. Třetí parametr, **envp**, je pole ukazatelů na proměnné prostředí. Pole **envp** je ukončeno ukazatelem s hodnotou null. Další informace o **Main** a **envp**najdete v tématu [hlavní funkce a spuštění programu](../c-language/main-function-and-program-execution.md) .

Proměnná **argc** nikdy nedrží zápornou hodnotu.

Pole řetězců končí řetězcem **argv [argc]**, který obsahuje ukazatel s hodnotou null.

Všechny prvky pole **argv** jsou ukazatele na řetězce.

Program vyvolaný bez argumentů příkazového řádku obdrží hodnotu jedna pro **argc**, protože název spustitelného souboru je umístěn v **argv [0]**. (V operačním systému MS-DOS verze dřívější než 3.0 není název spustitelného souboru k dispozici. Písmeno "C" je umístěno v **argv [0]**.) Řetězce, na které ukazuje **argv [1]** až **argv [argc-1]** , reprezentují parametry programu.

Parametry **argc** a **argv** lze upravovat a uchovávat jejich poslední uložené hodnoty mezi spuštěním programu a ukončením programu.

## <a name="see-also"></a>Viz také

[Prostředí](../c-language/environment.md)
