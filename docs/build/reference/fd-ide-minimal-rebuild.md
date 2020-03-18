---
title: /FD (minimální opětovné sestavení IDE)
ms.date: 04/08/2019
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: 896adcb97a259e6714cf23241424841456371491
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439816"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (minimální opětovné sestavení IDE)

**/FD** je zpřístupněna pouze uživatelům na stránce vlastností [příkazového řádku](command-line-property-pages.md) dialogového okna C++ **stránky vlastností** projektu. Je k dispozici pouze v případě, že není vybrána možnost nepoužívané a vypnuté ve výchozím nastavení [/GM (povolit minimální opětovné sestavení)](gm-enable-minimal-rebuild.md) . **/FD** nemá žádný vliv na jiné než vývojové prostředí. **/FD** není zveřejněné ve výstupu `cl /?`.

Pokud ve vývojovém prostředí nepovolíte možnost zastaralá **/GM** , použije se **/FD** . **/FD** zajistí, že soubor. IDB má dostatek informací o závislostech. **/FD** se používá pouze ve vývojovém prostředí a neměl by se používat z příkazového řádku nebo skriptu sestavení.

## <a name="see-also"></a>Viz také

[Možnosti výstupního souboru (/F)](output-file-f-options.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
