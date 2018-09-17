---
title: Vstupní soubory LINK | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5974914e736278ebb336b6814661845740855fe6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710232"
---
# <a name="link-input-files"></a>Vstupní soubory LINK

Zadejte linker se soubory, které obsahují objekty, importovat a standardní knihovny, prostředky, definice modulů a příkaz vstup. ODKAZ přípony souborů, abyste neklikli vytvářet předpoklady o obsah souboru. Místo toho odkaz zkontroluje každý vstupní soubor k určení, jaký druh souboru je.

Soubory objektů na příkazovém řádku se zpracovávají v pořadí, ve kterém se zobrazují na příkazovém řádku. Knihovny jsou prohledávány v pořadí příkazového řádku, s výstrahou, následující: nevyřešené symboly, které jsou při níž se přináší objektový soubor z knihovny se vyhledávají v této knihovně první a potom následující knihovny z příkazového řádku a [/DEFAULTLIB (zadat výchozí knihovnu)](../../build/reference/defaultlib-specify-default-library.md) direktivy a pak na žádné knihovny na začátek příkazového řádku.

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

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)