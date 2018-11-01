---
title: Závažná chyba C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: 3f4d152163d3b21ddf99644c34e63f35ca15e6e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457772"
---
# <a name="fatal-error-c1126"></a>Závažná chyba C1126

'identifier': automatické přidělování překračuje velikost

Místo přidělené pro místní proměnné funkce (včetně omezené množství využité kompilátorem, jako je například dalších 20 bajtů pro vyměnitelné funkce), překračuje limit.

Chcete-li opravit tuto chybu, použijte `malloc` nebo `new` přidělit velkých objemů dat.