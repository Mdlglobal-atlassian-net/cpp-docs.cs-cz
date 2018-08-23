---
title: U aplikací pro UPW, prostředí Windows Runtime a C Run-Time | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 356d6d8d-76ee-4181-9ad0-6f24b2fede38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78f76b6f61eb5d8e7370e61e9cc1f466bdfb4c43
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592716"
---
# <a name="uwp-apps-the-windows-runtime-and-the-c-run-time"></a>U aplikací pro UPW, prostředí Windows Runtime a C Run-Time

Univerzální aplikace pro platformu Windows (UPW) jsou programy, které běží v modulu Windows Runtime, který se spustí v systému Windows 8. Modul Windows Runtime se odvíjí od důvěryhodného prostředí, které řídí funkce, proměnné a prostředky, které jsou k dispozici pro aplikace pro UPW. Záměrné, zabránit modulu Windows Runtime omezení použití většiny funkcí knihovny Run-Time C (CRT) v aplikacích pro UPW.

Modul Windows Runtime nepodporuje následující funkce CRT:

- Většina funkcí CRT, které se týkají nepodporované funkce.

   Například nelze vytvořit proces pomocí aplikace pro UPW **exec** a **vytvořit podřízený proces** rodiny rutin.

   Když se v aplikaci UWP, že je skutečnost uvedena v článku o jeho nepodporuje funkce CRT.

- Většina vícebajtové znakové a řetězcové funkce.

   Text kódování Unicode a ANSI jsou však podporovány.

- Aplikace konzoly a argumenty příkazového řádku.

   Aplikace klasické pracovní plochy, ale stále podporu konzoly a argumenty příkazového řádku.

- Proměnné prostředí.

- Koncept aktuálního pracovního adresáře.

- UPW aplikace a knihovny DLL, které jsou staticky propojeny CRT a vytvořené s použitím [/MT](../build/reference/md-mt-ld-use-run-time-library.md) nebo `/MTd` – možnosti kompilátoru.

   To znamená, aplikaci, která se použije vícevláknovou statickou verzi CRT.

- Aplikace, která je vytvořená pomocí [/MDd](../build/reference/md-mt-ld-use-run-time-library.md) – možnost kompilátoru.

   To znamená, ladění, Vícevláknová a knihovnu DLL verzi CRT. V modulu Windows Runtime nepodporuje takové aplikace.

Úplný seznam funkcí CRT, které nejsou k dispozici v aplikaci UPW a návrhů týkajících se alternativní funkcí najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="see-also"></a>Viz také

[Kompatibilita](../c-runtime-library/compatibility.md)<br/>
[Nepodporované funkce CRT prostředí Windows Runtime](../c-runtime-library/windows-runtime-unsupported-crt-functions.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
