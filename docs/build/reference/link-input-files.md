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
ms.openlocfilehash: aec71d4622821618f377953d36a9676e2233eefc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328207"
---
# <a name="link-input-files"></a>Vstupní soubory LINK

Propojovací program poskytujete souborům, které obsahují objekty, importu a standardní knihovny, prostředky, definice modulů a vstup příkazu. ODKAZ nepoužívá přípony souborů k vytvoření předpokladů o obsahu souboru. Místo toho LINK zkontroluje každý vstupní soubor k určení, jaký druh souboru je.

Soubory objektů na příkazovém řádku jsou zpracovávány v pořadí, v jakém se zobrazují na příkazovém řádku. Knihovny jsou prohledávány také v příkazovém řádku s následující upozornění: Symboly, které nejsou vyřešeny při podání souboru objektu z knihovny, jsou nejprve vyhledávány v této knihovně a pak následující knihovny z příkazového řádku a [/DEFAULTLIB (Zadat výchozí knihovnu)](defaultlib-specify-default-library.md) direktivy a potom do všech knihoven na začátku příkazového řádku.

> [!NOTE]
> LINK již nepřijímá středník (nebo jiný znak) jako začátek komentáře v souborech odpovědí a souborech objednávek. Středníky jsou rozpoznány pouze jako začátek komentáře v souborech definice modulu (.def).

LINK používá následující typy vstupních souborů:

- [.obj soubory](dot-obj-files-as-linker-input.md)

- [Soubory .netmodule](netmodule-files-as-linker-input.md)

- [Soubory LIB](dot-lib-files-as-linker-input.md)

- [Soubory EXP](dot-exp-files-as-linker-input.md)

- [Soubory DEF](dot-def-files-as-linker-input.md)

- [Soubory PDB](dot-pdb-files-as-linker-input.md)

- [Soubory res](dot-res-files-as-linker-input.md)

- [Soubory EXE](dot-exe-files-as-linker-input.md)

- [Soubory TXT](dot-txt-files-as-linker-input.md)

- [Soubory ILK](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Viz také

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti propojovacího zařízení MSVC](linker-options.md)
