---
title: Výběr formátu vstupních souborů .netmodule
ms.date: 11/04/2016
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
ms.openlocfilehash: b4d4b80e4b9195d184b9d97cea67bbaaa3d7d843
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320565"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>Výběr formátu vstupních souborů .netmodule

Soubor MSIL .obj (zkompilovaný s [/clr](clr-common-language-runtime-compilation.md)) lze také použít jako soubor .netmodule.  .obj soubory obsahují metadata a nativní symboly.  Moduly .netmoduly obsahují pouze metadata.

Soubor MSIL .obj můžete předat libovolnému kompilátoru sady Visual Studio pomocí možnosti kompilátoru /addmodule (ale uvědomte si, že soubor OBJ se stane součástí výsledného sestavení a musí být dodán se sestavením).  Například Visual C# a Visual Basic mají možnost kompilátoru /addmodule.

> [!NOTE]
> Ve většině případů budete muset předat linkeru soubor OBJ z kompilace, která vytvořila modul .net.  Předání souboru modulu .dll nebo .netmodule MSIL do propojovacího programu může mít za následek LNK1107.

.obj soubory, spolu s jejich přidružené soubory .h, které odkazujete prostřednictvím #include ve zdroji, umožňují aplikacím Jazyka C++ využívat nativní typy v modulu, zatímco v souboru .netmodule mohou být aplikace jazyka C++ spotřebovány pouze spravované typy.  Pokud se pokusíte předat soubor OBJ #using, nebudou k dispozici informace o nativních typech. #include soubor u .obj .h souboru .

Jiné kompilátory sady Visual Studio mohou využívat pouze spravované typy z modulu.

Pomocí následujícího příkazu určete, zda je třeba použít soubor .netmodule nebo .obj jako vstup modulu do propojovacího systému MSVC:

- Pokud vytváříte s kompilátorem sady Visual Studio než Visual C++, zhotovte modul .netmodule a použijte modul .netmodule jako vstup do propojovacího programu.

- Pokud používáte kompilátor MSVC k výrobě modulů a moduly budou použity k vytvoření něčeho jiného než knihovny, použijte soubory OBJ vytvořené kompilátorem jako vstup modulu do propojovacího zařízení; nepoužívejte jako vstup soubor .netmodule.

- Pokud budou vaše moduly použity k vytvoření nativní (nikoli spravované) knihovny, použijte soubory OBJ jako vstup modulu do propojního a vygenerujte soubor knihovny LIB.

- Pokud budou vaše moduly použity k vytvoření spravované knihovny a všechny vstupy modulu do propojovacího programu budou ověřitelné (vyrobené s /clr:safe), použijte soubory OBJ jako vstup modulu do propojovacího zařízení a vygenerujte soubor knihovny .dll (assembly) nebo .netmodule (module).

- Pokud vaše moduly budou použity k vytvoření spravované knihovny a pokud jeden nebo více modulů vstup do propojovacího programu bude vytvořen pouze /clr, použijte .obj soubory jako vstup modulu do propojovacího programu a generovat .dll (sestavení).  Pokud chcete zpřístupnit spravované typy z knihovny a chcete také, aby aplikace jazyka C++ spotřebovávaly nativní typy v knihovně, bude knihovna skládat soubory OBJ pro moduly komponent knihovny (budete také chtít dodávat soubory H pro každý modul, aby na ně bylo možné odkazovat #include ze zdrojového kódu).

## <a name="see-also"></a>Viz také

[Soubory .netmodule jako vstup linkeru](netmodule-files-as-linker-input.md)
