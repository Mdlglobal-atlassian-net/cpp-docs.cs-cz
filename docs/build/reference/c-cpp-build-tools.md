---
title: Nástroje sestavení C/C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- c.build
dev_langs:
- C++
helpviewer_keywords:
- builds [C++], C/C++ tools
- tools [C++], build
ms.assetid: 48d9daf4-6bbf-473a-8ce2-bf2923b69f80
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a6a223e092e7ad31dd263142d2a87712eaf556b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726034"
---
# <a name="cc-build-tools"></a>Nástroje sestavení C/C++

Visual C++ poskytuje následující nástroje příkazového řádku pro zobrazení nebo manipulace s výstup sestavení:

- [BSCMAKE. Soubor EXE](../../build/reference/bscmake-reference.md) : sestavení souboru informace o procházení (.bsc), který obsahuje informace o symbolech (tříd, funkcí, dat, makra a typy) ve svém programu. Tyto informace zobrazit v systému windows vyhledejte ve vývojovém prostředí. (Soubor .bsc je možné také sestavit ve vývojovém prostředí.)

- [LIB. Soubor EXE](../../build/reference/lib-reference.md) slouží k vytváření a správě knihovny objektových souborů Common Object File Format (COFF). To lze použít také k vytváření soubory exportu a importu knihovny na odkaz exportovat definice.

- [EDITBIN –. Soubor EXE](../../build/reference/editbin-reference.md) se používá k úpravě binární soubory COFF.

- [DUMPBIN. Soubor EXE](../../build/reference/dumpbin-reference.md) zobrazí informace COFF binárních souborů (jako je například tabulka symbolů).

- [NMAKE](../../build/nmake-reference.md) načte a spustí soubory pravidel.

- [Errlook –](../../build/reference/value-edit-control.md), nástroj vyhledávání chyby načte modul chybová zpráva, která je založena na hodnotě zadané nebo chybovou zprávu systému.

## <a name="see-also"></a>Viz také

[Referenční zdroje k sestavení programu v jazyce C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Dekorované názvy](../../build/reference/decorated-names.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)