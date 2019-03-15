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
ms.openlocfilehash: 323a0045ab11f23ab996d5179a135d0eb4184f20
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817436"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (minimální opětovné sestavení IDE)

**/FD** nezveřejňují uživatelům s výjimkou v [příkazového řádku](command-line-property-pages.md) stránku vlastností projektu C++ **stránky vlastností** dialogové okno, pokud a pouze v případě [/Gm (povolení minimálního opětovného sestavení)](gm-enable-minimal-rebuild.md) zároveň nevyberete. **/FD** nemá žádný vliv jiné než z vývojového prostředí. **/FD** nezveřejňují v rámci výstupu **cl /?**.

Pokud nepovolíte **/Gm** ve vývojovém prostředí **/FD** se použije. **/FD** zajišťuje, že souboru IDB má dostatek informací o závislostech. **/FD** slouží pouze ve vývojovém prostředí a neměl by se používat z příkazového řádku nebo skriptu sestavení.

## <a name="see-also"></a>Viz také:

[Možnosti výstupního souboru (/F)](output-file-f-options.md)<br/>
[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
