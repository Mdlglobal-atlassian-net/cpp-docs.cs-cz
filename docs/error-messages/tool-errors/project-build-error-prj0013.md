---
title: Chyba sestavení projektu PRJ0013
ms.date: 11/04/2016
f1_keywords:
- PRJ0013
helpviewer_keywords:
- PRJ0013
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
ms.openlocfilehash: 868b50bdac3931465103b6b4893f7bc4d030c16d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359446"
---
# <a name="project-build-error-prj0013"></a>Chyba sestavení projektu PRJ0013

Systémový prostředek může být kriticky nízký. Nelze vytvořit kanál požadovaný ke spuštění sestavení.

Tato chyba označuje, že není dostatek systémových prostředků. Chcete-li vyřešit tuto chybu, snížit využití systémových prostředků jiné procesy aplikace.

K této chybě může dojít také úroveň zabezpečení není dostatečná k vytváření kanálů (viz [CreatePipe](https://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)).