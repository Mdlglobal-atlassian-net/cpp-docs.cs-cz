---
title: Chyba matematické operace M6202
ms.date: 11/04/2016
f1_keywords:
- M6202
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
ms.openlocfilehash: b8a3a4ab87a410c4cee8f7e4a1a0517c169d0364
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173657"
---
# <a name="math-error-m6202"></a>Chyba matematické operace M6202

' function ': Chyba _SING

Argument dané funkce byl hodnota pro tuto funkci v jednotném formátu. Funkce není definována pro tento argument.

Tato chyba volá funkci `_matherr` s názvem funkce, jejími argumenty a typem chyby. Můžete přepsat funkci `_matherr` a přizpůsobit tak zpracování určitých matematických chyb s plovoucí desetinnou čárkou v době běhu.
