---
title: Syntaxe názvu souboru CL
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
ms.openlocfilehash: 929096ed169a33e0876c3afb68f3594757d61e4e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438932"
---
# <a name="cl-filename-syntax"></a>Syntaxe názvu souboru CL

CL přijímá soubory s názvy, které dodržují konvence vytváření názvů systému souborů FAT, HPFS nebo systému souborů NTFS. Některý název souboru může obsahovat celé nebo jeho část cesty. Úplná cesta obsahuje název jednotky a jeden nebo více názvů adresářů. CL přijímá názvy souborů oddělených buď zpětná lomítka (\\) nebo lomítka (/). Názvy souborů, které obsahují mezery, musejí být uzavřeny do dvojitých uvozovek. Část cesty vynechá název jednotky, které CL předpokládá, že se aktuální jednotku. Pokud nezadáte cestu, CL předpokládá, že se soubor nachází v aktuálním adresáři.

Přípona názvu souboru Určuje, jak se soubory zpracují. Soubory C a C++, které mají přípony .c, .cxx nebo .cpp, jsou zkompilovány. Další soubory, včetně soubory .obj a knihoven (.lib), soubory definice modulu (.def), jsou linkeru předány bez právě zpracovává.

## <a name="see-also"></a>Viz také

[Syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md)