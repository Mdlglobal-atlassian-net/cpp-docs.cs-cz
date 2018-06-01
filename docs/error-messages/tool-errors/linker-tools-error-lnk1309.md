---
title: Chyba linkerů Lnk1309 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1309
dev_langs:
- C++
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ffecdc891a9fe0d1c17d6e36c87f5df10b449ec
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704095"
---
# <a name="linker-tools-error-lnk1309"></a>Chyba linkerů LNK1309

> *Type1* modulu bylo zjištěno; neplatný s přepínače /CLRIMAGETYPE:*type2*

## <a name="remarks"></a>Poznámky

Typ obrázku CLR byl vyžádán pomocí **/CLRIMAGETYPE** ale linkeru nemohl vytvořit image daného typu, protože jeden nebo více modulů byly kompatibilní s daným typem.

Například uvidíte LNK1309, pokud zadáte **/CLRIMAGETYPE:safe** a předejte modul vytvořené s **/CLR: pure**.

**/CLR: pure** a **/CLR: safe** kompilátoru možnosti a podpory knihovny, jsou zastaralé v sadě Visual Studio 2015 a jaké Visual Studio 2017.

Zobrazí se také LNK1309 při vytvoření částečně důvěryhodné aplikace čistý CLR pomocí .lib ptrustu [d]. Informace o tom, jak vytvořit částečně důvěryhodné aplikace najdete v tématu [postupy: Vytvoření částečně důvěryhodné aplikace odebrání závislostí na knihovnu DLL knihovny CRT](../../dotnet/create-a-partially-trusted-application.md).

Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [/CLRIMAGETYPE (zadat typ z obrázku CLR)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).