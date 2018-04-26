---
title: Aplikace UWP, prostředí Windows Runtime a C Run-Time | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 356d6d8d-76ee-4181-9ad0-6f24b2fede38
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e9e6053cdcd7797319379e1e5e7290bcff373b6f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="uwp-apps-the-windows-runtime-and-the-c-run-time"></a>Aplikace UWP, prostředí Windows Runtime a běhu C

Univerzální aplikace pro platformu Windows (UWP) jsou programy, které běží v prostředí Windows Runtime, který je prováděn [!INCLUDE[win8](../build/reference/includes/win8_md.md)]. Prostředí Windows Runtime je důvěryhodného prostředí, které řídí funkce, proměnné a prostředky, které jsou k dispozici pro aplikace pro UPW. Návrh zabránit prostředí Windows Runtime omezení použití většinu funkcí běhové knihovny jazyka C (CRT) v aplikacích pro UPW.

Prostředí Windows Runtime nepodporuje následující funkce CRT:

- Většina funkcí CRT, které se vztahují k nepodporované funkce.

   Například nelze vytvořit proces pomocí aplikace pro UPW **exec** a **spawn** rodiny rutiny.

   Když funkce CRT nepodporuje aplikace pro UPW, že je skutečnost uvedena v článku o jeho.

- Většina vícebajtové znaky a řetězce funkce.

   Kódování Unicode a ANSI text jsou však podporovány.

- Aplikace konzoly a argumenty příkazového řádku.

   Tradiční aplikace klasické pracovní plochy však stále podporují konzoly a argumenty příkazového řádku.

- Proměnné prostředí.

- Koncept aktuální pracovní adresář.

- UWP aplikace a knihovny DLL, které jsou staticky propojené s CRT a sestaveny pomocí tohoto [/MT](../build/reference/md-mt-ld-use-run-time-library.md) nebo `/MTd` – možnosti kompilátoru.

   To znamená, aplikaci, která používá s více vlákny, statické verzi CRT.

- Aplikace vytvořené pomocí [/MDd](../build/reference/md-mt-ld-use-run-time-library.md) – možnost kompilátoru.

   To znamená, ladění, vícevláknový a verze specifické DLL Knihovny CRT. Tato aplikace není podporována v prostředí Windows Runtime.

Úplný seznam funkcí CRT, které nejsou k dispozici v aplikaci UWP a návrhy pro alternativní funkce najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="see-also"></a>Viz také

[Kompatibilita](../c-runtime-library/compatibility.md)<br/>
[Nepodporované funkce CRT prostředí Windows Runtime](../c-runtime-library/windows-runtime-unsupported-crt-functions.md)<br/>
[Univerzální C runtime rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
