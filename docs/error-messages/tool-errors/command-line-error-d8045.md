---
title: Chyba příkazového řádku D8045
ms.date: 11/04/2016
f1_keywords:
- D8045
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
ms.openlocfilehash: 7964c2539b5358d2d946e530c4ee75110857446d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214193"
---
# <a name="command-line-error-d8045"></a>Chyba příkazového řádku D8045

Soubor C 'file' s možností/CLR nelze zkompilovat.

Mohou být předány pouze soubory zdrojového kódu C++ kompilaci, která používá **/CLR**.  Použití **/TP** ke kompilaci souboru .c jako souboru s příponou .cpp, naleznete v tématu [/Tc /Tp /TC, /TP (určení typu zdrojového souboru)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) Další informace.

Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

D8045 může také dojít, pokud kompilujete aplikace ATL s použitím Visual C++. Zobrazit [jak: Přechod na/CLR](../../dotnet/how-to-migrate-to-clr.md) Další informace.