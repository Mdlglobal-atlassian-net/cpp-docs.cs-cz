---
title: Chyba linkerů LNK1309
ms.date: 11/04/2016
f1_keywords:
- LNK1309
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
ms.openlocfilehash: ea675ca835dfc3fe4881e5fabbea746a4442b10a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187440"
---
# <a name="linker-tools-error-lnk1309"></a>Chyba linkerů LNK1309

> *Type1* modulu detekoval se neplatný pomocí přepínače/CLRIMAGETYPE:*typ2*

## <a name="remarks"></a>Poznámky

Typ bitové kopie CLR byl vyžádán pomocí **/CLRIMAGETYPE** ale linkeru nelze vytvořit bitovou kopii tohoto typu, protože jeden nebo více modulů byly kompatibilní s tímto typem.

Například uvidíte LNK1309, pokud zadáte **safe** a předáte moduly sestavené s **/CLR: pure**.

**/CLR: pure** a **/CLR: safe** knihovny kompilátoru možnosti a možnosti podpory jsou zastaralé v sadě Visual Studio 2015 a není podporován v sadě Visual Studio 2017.

Zobrazí se také LNK1309 při pokusu o vytvoření částečně důvěryhodné aplikace čistě CLR pomocí lib ptrustu [d]. Informace o tom, jak vytvořit částečně důvěryhodné aplikace najdete v tématu [jak: Vytvoření částečně důvěryhodné aplikace odebráním závislosti na knihovně DLL knihovny CRT](../../dotnet/create-a-partially-trusted-application.md).

Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [/CLRIMAGETYPE (zadat typ z bitové kopie modulu CLR)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).