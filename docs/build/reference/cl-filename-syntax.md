---
title: Syntaxe názvu souboru CL
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
ms.openlocfilehash: 1135e5c682b79fec5de808b61c93d370f05a3aa9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440235"
---
# <a name="cl-filename-syntax"></a>Syntaxe názvu souboru CL

CL akceptuje soubory s názvy, které následují zásady vytváření názvů v systému souborů FAT, HPFS nebo NTFS. Libovolný název souboru může obsahovat úplnou nebo částečnou cestu. Úplná cesta obsahuje název jednotky a jeden nebo více názvů adresářů. CL přijímá názvy souborů oddělené zpětným lomítkem (\\) nebo lomítkem (/). Názvy souborů, které obsahují mezery, musí být obklopeny znaky dvojité uvozovky. Částečná cesta vynechá název jednotky, který CL předpokládá jako aktuální jednotku. Pokud nezadáte cestu, CL předpokládá, že soubor je v aktuálním adresáři.

Přípona názvu souboru určuje způsob zpracování souborů. Soubory C C++ a, které mají příponu. c,. příponu CXX nebo. cpp, jsou kompilovány. Jiné soubory, včetně souborů. obj, knihoven (. lib) a souborů definice modulu (. def), jsou předány do linkeru bez zpracování.

## <a name="see-also"></a>Viz také

[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
