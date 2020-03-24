---
title: Chyba linkerů LNK2011
ms.date: 11/04/2016
f1_keywords:
- LNK2011
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
ms.openlocfilehash: e08f068099af68375523eae0f0cc4d63960f3261
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194808"
---
# <a name="linker-tools-error-lnk2011"></a>Chyba linkerů LNK2011

předkompilovaný objekt není propojen. Image se možná nespustí.

Použijete-li předkompilované hlavičky, odkaz vyžaduje, aby všechny soubory objektů vytvořené pomocí předkompilovaných hlaviček měly být propojeny v. Máte-li zdrojový soubor, který použijete k vygenerování předkompilované hlavičky pro použití s jinými zdrojovými soubory, je nyní nutné zahrnout soubor objektů vytvořený společně s předkompilovanou hlavičkou.

Například pokud kompilujete soubor s názvem STUB. cpp pro vytvoření předkompilované hlavičky pro použití s jinými zdrojovými soubory, musíte propojit se zástupným procedurou. obj nebo se zobrazí tato chyba. Na následujících příkazových řádcích se jeden řádek používá k vytvoření předkompilované hlavičky COMMON. pch, která se používá s PROG1. cpp a PROG2. cpp na řádcích dva a tři. Soubor STUB. cpp obsahuje pouze `#include` řádky (stejné `#include` řádky jako v PROG1. cpp a PROG2. cpp) a slouží pouze ke generování předkompilovaných hlaviček. V posledním řádku musí být objekt STUB. obj propojen, aby nedošlo k LINKERŮ LNK2011.

```
cl /c /Yccommon.h stub.cpp
cl /c /Yucommon.h prog1.cpp
cl /c /Yucommon.h prog2.cpp
link /out:prog.exe stub.obj prog1.obj prog2.obj
```
