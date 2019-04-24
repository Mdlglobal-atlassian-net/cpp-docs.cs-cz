---
title: /FD (minimální opětovné sestavení IDE)
ms.date: 04/08/2019
f1_keywords:
- /FD
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: ac63b021dc0cb9ee5964af7fa2e168f710653979
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292871"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (minimální opětovné sestavení IDE)

**/FD** je dostupná jenom v případě uživatelům [příkazového řádku](command-line-property-pages.md) na stránce vlastností C++ projektu **stránky vlastností** dialogové okno. Je k dispozici pokud a pouze v případě zastaralé a vypnout výchozím [/Gm (povolení minimálního opětovného sestavení)](gm-enable-minimal-rebuild.md) možnost není vybraná. **/FD** nemá žádný vliv jiné než z vývojového prostředí. **/FD** nezveřejňují v rámci výstupu `cl /?`.

Pokud nepovolíte zastaralá **/Gm** možnost ve vývojovém prostředí **/FD** se používá. **/FD** zajišťuje souboru IDB má dostatek informací o závislostech. **/FD** slouží pouze ve vývojovém prostředí a neměl by se používat z příkazového řádku nebo skriptu sestavení.

## <a name="see-also"></a>Viz také:

[Možnosti výstupního souboru (/F)](output-file-f-options.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
