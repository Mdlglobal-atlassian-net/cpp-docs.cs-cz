---
title: "Syntaxe názvu souboru CL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cl
dev_langs: C++
helpviewer_keywords:
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 95cce7367eac5e4637d148b2c54cd5271f4f3026
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cl-filename-syntax"></a>Syntaxe názvu souboru CL
CL přijímá soubory s názvy, které následují zásady vytváření názvů systému souborů FAT, HPFS nebo systému souborů NTFS. Libovolný název souboru může obsahovat úplné nebo částečné cesty. Úplná cesta zahrnuje název jednotky a jeden nebo více názvů adresářů. CL přijímá názvy souborů oddělené buď zpětná lomítka (\\) nebo předávat lomítka (/). Názvy souborů, které obsahují mezery, musí být uzavřena do dvojitých uvozovek. Část cesty vynechá název jednotky, které CL předpokládá, že se aktuální jednotku. Pokud nezadáte cestu, CL předpokládá, že soubor je v aktuálním adresáři.  
  
 Přípona názvu souboru Určuje, jak se zpracují soubory. C a C++ soubory, které mají rozšíření .c, .cxx nebo sada, jsou zkompilovat. Další soubory, včetně .obj soubory, knihovny (LIB) a soubory definice modulu (.def), jsou předány linkeru bez zpracovává.  
  
## <a name="see-also"></a>Viz také  
 [Syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md)