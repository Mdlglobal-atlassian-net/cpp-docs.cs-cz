---
title: Závažná chyba C1352
ms.date: 11/04/2016
f1_keywords:
- C1352
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
ms.openlocfilehash: 07bd0f28e35dd2992ca537dbe744d756cc2afe80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203122"
---
# <a name="fatal-error-c1352"></a>Závažná chyba C1352

Neplatný nebo poškozený jazyk MSIL ve funkci Function z modulu File

Do kompilátoru byl předán objekt. netmodule, ale Kompilátor zjistil v souboru poškození.  Požádejte osobu, která vytvořila modul. netmodule k prozkoumání.

Kompilátor nekontroluje soubory. netmodule pro všechny typy poškození.  Ale zkontroluje, že všechny cesty k ovládacím prvkům ve funkci obsahují příkaz return.

Další informace naleznete v tématu [soubory. netmodule jako vstup linkeru](../../build/reference/netmodule-files-as-linker-input.md).
