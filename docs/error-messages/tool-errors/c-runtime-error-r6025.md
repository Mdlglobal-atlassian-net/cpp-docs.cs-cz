---
title: Chyba modulu Runtime R6025 C
ms.date: 11/04/2016
f1_keywords:
- R6025
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
ms.openlocfilehash: 461bfb2aa46053ec56fff67de70038b1fcd97389
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639559"
---
# <a name="c-runtime-error-r6025"></a>Chyba modulu Runtime R6025 C

volání čistě virtuální funkce

> [!NOTE]
> Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má vnitřní problém. Nejčastější příčinou této chyby je chyba v aplikaci nebo poškozená instalace.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> - Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> - Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Žádný objekt po vytvoření instance, pro zpracování volání čistě virtuální funkce.

Tato chyba je způsobena volání virtuální funkce v abstraktní základní třída přes ukazatel, který je vytvořen pomocí přetypování na typ odvozené třídy, ale je ukazatelem na základní třídu. Tato situace může nastat při přetypování z: **void** <strong>\*</strong> na ukazatel na třídu při **void** <strong>\*</strong> byl vytvořené během procesu vytváření základní třídy.

