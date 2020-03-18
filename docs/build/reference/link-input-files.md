---
title: Vstupní soubory LINK
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], LINK
- module definition files
- resources [C++], linker files
- LINK tool [C++], input files
- module definition files, linker files
- input files [C++], LINK
- linker [C++], input files
- import libraries [C++], linker files
- command input to linker files [C++]
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
ms.openlocfilehash: 25d8e20903a97186e2c32a079fd74ece3626b7fa
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439339"
---
# <a name="link-input-files"></a>Vstupní soubory LINK

Do linkeru zadáte soubory, které obsahují objekty, import a standardní knihovny, prostředky, definice modulů a vstup příkazů. ODKAZ nepoužívá přípony souborů k vytvoření předpokladů o obsahu souboru. Místo toho odkaz prověřuje každý vstupní soubor a určí, jaký typ souboru je.

Soubory objektů na příkazovém řádku jsou zpracovávány v pořadí, v jakém jsou uvedeny na příkazovém řádku. Knihovny jsou prohledávány v pořadí příkazového řádku, a to s následujícími omezeními: nevyřešené symboly při uvádění do souborového souboru z knihovny jsou nejprve prohledány v této knihovně a poté následující knihovny z příkazového řádku a [/DEFAULTLIB (určení výchozích knihoven)](defaultlib-specify-default-library.md) a následně do jakékoli knihovny na začátku příkazového řádku.

> [!NOTE]
>  ODKAZ už nepřijímá středník (ani jiný znak) jako začátek komentáře v souborech odpovědí a souborech objednávek. Středníky jsou rozpoznány pouze jako začátek komentářů v souborech definice modulu (. def).

ODKAZ používá následující typy vstupních souborů:

- [soubory. obj](dot-obj-files-as-linker-input.md)

- [soubory. netmodule](netmodule-files-as-linker-input.md)

- [soubory. lib](dot-lib-files-as-linker-input.md)

- [soubory. exp](dot-exp-files-as-linker-input.md)

- [soubory. def](dot-def-files-as-linker-input.md)

- [soubory. pdb](dot-pdb-files-as-linker-input.md)

- [soubory. res](dot-res-files-as-linker-input.md)

- [soubory. exe](dot-exe-files-as-linker-input.md)

- [soubory. txt](dot-txt-files-as-linker-input.md)

- [soubory. ilk](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Viz také

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
