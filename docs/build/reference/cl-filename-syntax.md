---
title: Syntaxe názvu souboru CL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04d82be73f2e73a24daeabd6219abdeadcb4cbbf
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716882"
---
# <a name="cl-filename-syntax"></a>Syntaxe názvu souboru CL

CL přijímá soubory s názvy, které dodržují konvence vytváření názvů systému souborů FAT, HPFS nebo systému souborů NTFS. Některý název souboru může obsahovat celé nebo jeho část cesty. Úplná cesta obsahuje název jednotky a jeden nebo více názvů adresářů. CL přijímá názvy souborů oddělených buď zpětná lomítka (\\) nebo lomítka (/). Názvy souborů, které obsahují mezery, musejí být uzavřeny do dvojitých uvozovek. Část cesty vynechá název jednotky, které CL předpokládá, že se aktuální jednotku. Pokud nezadáte cestu, CL předpokládá, že se soubor nachází v aktuálním adresáři.

Přípona názvu souboru Určuje, jak se soubory zpracují. Soubory C a C++, které mají přípony .c, .cxx nebo .cpp, jsou zkompilovány. Další soubory, včetně soubory .obj a knihoven (.lib), soubory definice modulu (.def), jsou linkeru předány bez právě zpracovává.

## <a name="see-also"></a>Viz také

[Syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md)