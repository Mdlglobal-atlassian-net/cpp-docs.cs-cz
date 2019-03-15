---
title: Vstupní soubory LINK
ms.date: 11/04/2016
f1_keywords:
- link
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
ms.openlocfilehash: 48ad9423ae35c22a97a873fe6a2a0479c12ab33b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817787"
---
# <a name="link-input-files"></a>Vstupní soubory LINK

Zadejte linker se soubory, které obsahují objekty, importovat a standardní knihovny, prostředky, definice modulů a příkaz vstup. ODKAZ přípony souborů, abyste neklikli vytvářet předpoklady o obsah souboru. Místo toho odkaz zkontroluje každý vstupní soubor k určení, jaký druh souboru je.

Soubory objektů na příkazovém řádku se zpracovávají v pořadí, ve kterém se zobrazují na příkazovém řádku. Knihovny jsou prohledávány v pořadí příkazového řádku, s výstrahou, následující: Nevyřešené symboly, které jsou při níž se přináší objektový soubor z knihovny se vyhledávají v této knihovně první a potom následující knihovny z příkazového řádku a [/DEFAULTLIB (zadat výchozí knihovnu)](defaultlib-specify-default-library.md) direktivy a pak na žádné knihovny na začátek příkazového řádku.

> [!NOTE]
>  ODKAZ již přijímá středník (nebo jakýkoli jiný znak) jako začátek komentáře v souborech odpovědí a soubory pořadí. Středníky jsou rozpoznány pouze jako začátek komentáře v souborech definice modulu (.def).

ODKAZ používá následující typy vstupních souborů:

- [soubory .obj](dot-obj-files-as-linker-input.md)

- [soubory .netmodule](netmodule-files-as-linker-input.md)

- [soubory .lib](dot-lib-files-as-linker-input.md)

- [soubory .exp](dot-exp-files-as-linker-input.md)

- [soubory .def](dot-def-files-as-linker-input.md)

- [soubory s příponou .pdb](dot-pdb-files-as-linker-input.md)

- [soubory .res](dot-res-files-as-linker-input.md)

- [soubory .exe](dot-exe-files-as-linker-input.md)

- [soubory s příponou .txt](dot-txt-files-as-linker-input.md)

- [soubory .ilk](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
