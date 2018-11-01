---
title: Argumenty operace main
ms.date: 11/04/2016
ms.assetid: 39824fef-05ad-461d-ae82-49447dda8060
ms.openlocfilehash: 52361c4347ee7c55b98bcacb4759bb79d53cb73e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638786"
---
# <a name="arguments-to-main"></a>Argumenty operace main

**ANSI 2.1.2.2.1** sémantiku argumenty operace Main

V Microsoft C je volána funkce volá se při spuštění programu **hlavní**. Neexistuje žádný prototyp pro deklarovaný **hlavní**, a lze ji definovat s žádným, dvěma nebo třemi parametry:

```
int main( void )
int main( int argc, char *argv[] )
int main( int argc, char *argv[], char *envp[] )
```

Třetí řádek výše, kde **hlavní** přijímá tři parametry, je rozšíření standardu ANSI C společnosti Microsoft. Třetí parametr **envp**, je pole ukazatelů na proměnné prostředí. **Envp** pole je ukončeno nulovým ukazatelem. Zobrazit [– funkce main a vykonávání programu](../c-language/main-function-and-program-execution.md) Další informace o **hlavní** a **envp**.

Proměnná **argc** nikdy neudržuje zápornou hodnotu.

Pole řetězců končí **argv [argc]**, který obsahuje ukazatel s hodnotou null.

Všechny prvky **argv** pole jsou ukazatele na řetězce.

Program spuštěný bez argumentů příkazového řádku se zobrazí hodnota objektu pro **argc**, protože název spustitelného souboru, který je umístěn ve **argv [0]**. (V operačním systému MS-DOS verze dřívější než 3.0 není název spustitelného souboru k dispozici. Písmeno "C", nachází ve **argv [0]**.) Řetězce, na **argv [1]** prostřednictvím **argv [argc - 1]** představují parametry programu.

Parametry **argc** a **argv** lze upravit a zachovávají své naposled uložené hodnoty od spuštění do ukončení programu.

## <a name="see-also"></a>Viz také

[Prostředí](../c-language/environment.md)