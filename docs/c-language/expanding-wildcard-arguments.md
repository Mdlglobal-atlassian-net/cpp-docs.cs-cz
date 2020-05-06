---
title: Rozbalení argumentů zástupných znaků
ms.date: 11/04/2016
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
ms.openlocfilehash: f1fb964fe98223fb7187b83c7101027ed1f9cbea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233804"
---
# <a name="expanding-wildcard-arguments"></a>Rozbalení argumentů zástupných znaků

**Specifické pro Microsoft**

Když spustíte program v jazyce C, můžete použít kterýkoli ze dvou zástupných znaků – otazník (?) a hvězdička (*) – pro zadání názvů filename a Path na příkazovém řádku.

Ve výchozím nastavení nejsou zástupné znaky rozbaleny v argumentech příkazového řádku. Můžete nahradit rutinu normálního `argv` načítání normální argument pomocí verze, která rozbalí zástupné znaky, propojením se souborem setargv. obj nebo wsetargv. obj. Pokud program používá `main` funkci, připojte se k setargv. obj. Pokud program používá `wmain` funkci, připojte se k wsetargv. obj. Oba mají stejné chování.

Chcete-li vytvořit propojení s setargv. obj nebo wsetargv. obj, použijte možnost **/Link** . Příklad:

**Příklad: c/Link setargv. obj**

Zástupné znaky se rozšíří stejným způsobem jako příkazy operačního systému. (Pokud neznáte zástupné znaky, přečtěte si uživatelskou příručku k operačnímu systému.)

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Možnosti propojení](../c-runtime-library/link-options.md)<br/>
[main – spuštění funkce a programu](../c-language/main-function-and-program-execution.md)
