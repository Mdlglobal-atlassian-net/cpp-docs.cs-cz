---
title: -FD (minimální opětovné sestavení IDE) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FD
dev_langs:
- C++
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74fb35ec25bed808e2165498c00b65723aba5bac
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702439"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (minimální opětovné sestavení IDE)

**/FD** nezveřejňují uživatelům s výjimkou v [příkazového řádku](../../ide/command-line-property-pages.md) stránku vlastností projektu C++ **stránky vlastností** dialogové okno, pokud a pouze v případě [/Gm (povolení minimálního opětovného sestavení)](../../build/reference/gm-enable-minimal-rebuild.md) zároveň nevyberete. **/FD** nemá žádný vliv jiné než z vývojového prostředí. **/FD** nezveřejňují v rámci výstupu **cl /?**.

Pokud nepovolíte **/Gm** ve vývojovém prostředí **/FD** se použije. **/FD** zajišťuje, že souboru IDB má dostatek informací o závislostech. **/FD** slouží pouze ve vývojovém prostředí a neměl by se používat z příkazového řádku nebo skriptu sestavení.

## <a name="see-also"></a>Viz také

[Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)
[– možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)