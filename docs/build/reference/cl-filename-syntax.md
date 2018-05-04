---
title: Syntaxe názvu souboru CL | Microsoft Docs
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
ms.openlocfilehash: 121cd8971be65e15ad6445cb347baf478046bf3e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cl-filename-syntax"></a>Syntaxe názvu souboru CL
CL přijímá soubory s názvy, které následují zásady vytváření názvů systému souborů FAT, HPFS nebo systému souborů NTFS. Libovolný název souboru může obsahovat úplné nebo částečné cesty. Úplná cesta zahrnuje název jednotky a jeden nebo více názvů adresářů. CL přijímá názvy souborů oddělené buď zpětná lomítka (\\) nebo předávat lomítka (/). Názvy souborů, které obsahují mezery, musí být uzavřena do dvojitých uvozovek. Část cesty vynechá název jednotky, které CL předpokládá, že se aktuální jednotku. Pokud nezadáte cestu, CL předpokládá, že soubor je v aktuálním adresáři.  
  
 Přípona názvu souboru Určuje, jak se zpracují soubory. C a C++ soubory, které mají rozšíření .c, .cxx nebo sada, jsou zkompilovat. Další soubory, včetně .obj soubory, knihovny (LIB) a soubory definice modulu (.def), jsou předány linkeru bez zpracovává.  
  
## <a name="see-also"></a>Viz také  
 [Syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md)