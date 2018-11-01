---
title: /FD (minimální opětovné sestavení IDE)
ms.date: 11/04/2016
f1_keywords:
- /FD
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: a902096bf13105e6a6a66b7bd3ccc56b8f7cf624
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433589"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (minimální opětovné sestavení IDE)

**/FD** nezveřejňují uživatelům s výjimkou v [příkazového řádku](../../ide/command-line-property-pages.md) stránku vlastností projektu C++ **stránky vlastností** dialogové okno, pokud a pouze v případě [/Gm (povolení minimálního opětovného sestavení)](../../build/reference/gm-enable-minimal-rebuild.md) zároveň nevyberete. **/FD** nemá žádný vliv jiné než z vývojového prostředí. **/FD** nezveřejňují v rámci výstupu **cl /?**.

Pokud nepovolíte **/Gm** ve vývojovém prostředí **/FD** se použije. **/FD** zajišťuje, že souboru IDB má dostatek informací o závislostech. **/FD** slouží pouze ve vývojovém prostředí a neměl by se používat z příkazového řádku nebo skriptu sestavení.

## <a name="see-also"></a>Viz také

[Možnosti výstupního souboru (/F)](../../build/reference/output-file-f-options.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)