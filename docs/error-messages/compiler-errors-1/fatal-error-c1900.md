---
title: Závažná chyba C1900 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1900
dev_langs:
- C++
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b2211b4243ddf44194959a263fd90ec1a615ea0a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220278"
---
# <a name="fatal-error-c1900"></a>Závažná chyba C1900

> IL – Neshoda mezi "*tool1*'version'*Číslo1*"a"*tool2*'version'*číslo2*.

Nástroje pro spuštění v různých průchody kompilátoru se neshodují. *Číslo1* a *číslo2* odkazují na data na souborech. Například v kroku 1, kompilátor front-end spuštění (c1.dll) a v kroku 2, kompilátor back-end spuštění (c2.dll). Data se soubory se musí shodovat.

Chcete-li vyřešit tento problém, ujistěte se, že všechny aktualizace se použily k sadě Visual Studio. Pokud se problém nevyřeší, použijte **programy a funkce** v Ovládacích panelech Windows opravte nebo přeinstalujte Visual Studio.