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
ms.openlocfilehash: 9fb2e6b8ee0f8ddc1512c605373671ae1c93c0b8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413248"
---
# <a name="link-input-files"></a>Vstupní soubory LINK

Zadejte linker se soubory, které obsahují objekty, importovat a standardní knihovny, prostředky, definice modulů a příkaz vstup. ODKAZ přípony souborů, abyste neklikli vytvářet předpoklady o obsah souboru. Místo toho odkaz zkontroluje každý vstupní soubor k určení, jaký druh souboru je.

Soubory objektů na příkazovém řádku se zpracovávají v pořadí, ve kterém se zobrazují na příkazovém řádku. Knihovny jsou prohledávány v pořadí příkazového řádku, s výstrahou, následující: Nevyřešené symboly, které jsou při níž se přináší objektový soubor z knihovny se vyhledávají v této knihovně první a potom následující knihovny z příkazového řádku a [/DEFAULTLIB (zadat výchozí knihovnu)](../../build/reference/defaultlib-specify-default-library.md) direktivy a pak na žádné knihovny na začátek příkazového řádku.

> [!NOTE]
>  ODKAZ již přijímá středník (nebo jakýkoli jiný znak) jako začátek komentáře v souborech odpovědí a soubory pořadí. Středníky jsou rozpoznány pouze jako začátek komentáře v souborech definice modulu (.def).

ODKAZ používá následující typy vstupních souborů:

- [soubory .obj](../../build/reference/dot-obj-files-as-linker-input.md)

- [soubory .netmodule](../../build/reference/netmodule-files-as-linker-input.md)

- [soubory .lib](../../build/reference/dot-lib-files-as-linker-input.md)

- [soubory .exp](../../build/reference/dot-exp-files-as-linker-input.md)

- [soubory .def](../../build/reference/dot-def-files-as-linker-input.md)

- [soubory s příponou .pdb](../../build/reference/dot-pdb-files-as-linker-input.md)

- [soubory .res](../../build/reference/dot-res-files-as-linker-input.md)

- [soubory .exe](../../build/reference/dot-exe-files-as-linker-input.md)

- [soubory s příponou .txt](../../build/reference/dot-txt-files-as-linker-input.md)

- [soubory .ilk](../../build/reference/dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
