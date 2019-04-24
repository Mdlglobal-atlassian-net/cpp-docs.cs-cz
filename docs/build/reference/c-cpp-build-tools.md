---
title: Nástroje pro vytváření dalších MSVC
ms.date: 11/04/2016
f1_keywords:
- c.build
helpviewer_keywords:
- builds [C++], C/C++ tools
- tools [C++], build
ms.assetid: 48d9daf4-6bbf-473a-8ce2-bf2923b69f80
ms.openlocfilehash: e41a6dcb8de4a8608d065cce5bce2595cd96a84f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272842"
---
# <a name="additional-msvc-build-tools"></a>Nástroje pro vytváření dalších MSVC

Visual C++ poskytuje následující nástroje příkazového řádku pro zobrazení nebo manipulace s výstup sestavení:


- [LIB. Soubor EXE](lib-reference.md) slouží k vytváření a správě knihovny objektových souborů Common Object File Format (COFF). To lze použít také k vytváření soubory exportu a importu knihovny na odkaz exportovat definice.

- [EDITBIN –. Soubor EXE](editbin-reference.md) se používá k úpravě binární soubory COFF.

- [DUMPBIN. Soubor EXE](dumpbin-reference.md) zobrazí informace COFF binárních souborů (jako je například tabulka symbolů).

- [NMAKE](nmake-reference.md) načte a spustí soubory pravidel.

- [Errlook –](value-edit-control.md), nástroj vyhledávání chyby načte modul chybová zpráva, která je založena na hodnotě zadané nebo chybovou zprávu systému.

- [Xdcmake –](xdcmake-reference.md). Toolfor zpracování souborů zdrojového kódu, které obsahují dokumentační komentáře se označí značky XML.

- [BSCMAKE. Soubor EXE](bscmake-reference.md) (k dispozici pouze z důvodů zpětné kompatibility): sestavení souboru informace o procházení (.bsc), který obsahuje informace o symbolech (tříd, funkcí, dat, makra a typy) ve svém programu. Tyto informace zobrazit v systému windows vyhledejte ve vývojovém prostředí. (Soubor .bsc je možné také sestavit ve vývojovém prostředí.)

## <a name="see-also"></a>Viz také:

[Referenční zdroje k sestavení programu v jazyce C/C++](c-cpp-building-reference.md)<br/>
[Dekorované názvy](decorated-names.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
