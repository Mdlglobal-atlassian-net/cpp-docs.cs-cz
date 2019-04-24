---
title: Závažná chyba C1900
ms.date: 11/04/2016
f1_keywords:
- C1900
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
ms.openlocfilehash: c4622dd4552f7bfcc822a3aab4d5783146d68ac7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165720"
---
# <a name="fatal-error-c1900"></a>Závažná chyba C1900

> IL – Neshoda mezi "*tool1*'version'*Číslo1*"a"*tool2*'version'*číslo2*.

Nástroje pro spuštění v různých průchody kompilátoru se neshodují. *Číslo1* a *číslo2* odkazují na data na souborech. Například v kroku 1, kompilátor front-end spuštění (c1.dll) a v kroku 2, kompilátor back-end spuštění (c2.dll). Data se soubory se musí shodovat.

Chcete-li vyřešit tento problém, ujistěte se, že všechny aktualizace se použily k sadě Visual Studio. Pokud se problém nevyřeší, použijte **programy a funkce** v Ovládacích panelech Windows opravte nebo přeinstalujte Visual Studio.