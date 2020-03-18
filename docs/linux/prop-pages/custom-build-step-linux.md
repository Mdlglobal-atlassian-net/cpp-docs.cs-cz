---
title: Vlastnosti vlastního kroku sestavení (Linux C++)
ms.date: 06/07/2019
ms.assetid: 77a9c1fb-7c41-4a9b-9418-18ac17ce4e74
ms.openlocfilehash: 67b281e245c4fff8f37baff8875cbc3dc84ca718
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441331"
---
# <a name="custom-build-step-properties-linux-c"></a>Vlastnosti vlastního kroku sestavení (Linux C++)

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range=">=vs-2017"

| Vlastnost | Popis |
|--|--|
| Příkazový řádek | Příkaz, který má vlastní krok sestavení provést. |
| Popis | Zpráva, která se zobrazí při spuštění vlastního kroku sestavení |
| Výstupy | Výstupní soubor, který je vygenerován vlastním krokem sestavení. Toto nastavení je povinné, aby přírůstkové sestavení fungovalo správně. |
| Další závislosti | Seznam případných dalších vstupních souborů, které se mají použít ve vlastním kroku sestavení, oddělených středníkem. |
| Provést po a provést před | Tyto volby definují, kdy se vlastní krok v rámci procesu sestavení spustí. Zadávají se ve vztahu k cílům uvedeným v seznamu. Nejčastěji používané cíle jsou BuildGenerateSources, BuildCompile a BuildLink, které představují nejdůležitější kroky v procesu sestavení. Další často používané cíle jsou Midl, CLCompile a Link. |
| Považovat výstup za obsah | Tato možnost je smysluplná jenom pro aplikace Microsoft Store nebo Windows Phone, které zahrnují všechny soubory obsahu v balíčku. appx. |

::: moniker-end
