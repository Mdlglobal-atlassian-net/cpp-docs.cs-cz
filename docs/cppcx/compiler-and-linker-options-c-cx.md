---
title: Možnosti kompilátoru a Linkeru (C + +/ CX)
ms.date: 01/22/2017
ms.assetid: ecfadce8-3a3f-40cc-bb01-b4731f8d2fcb
ms.openlocfilehash: 2165d802e6ff4bd530acac7c1ba6185c732a6499
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577281"
---
# <a name="compiler-and-linker-options-ccx"></a>Možnosti kompilátoru a Linkeru (C + +/ CX)

Proměnné prostředí, C + +/ CX – možnosti kompilátoru a linkeru možnosti podporu vytváření aplikací pro Windows Runtime.

## <a name="library-path"></a>Cestu ke knihovně

Proměnné prostředí % % LIBPATH Určuje výchozí cestu pro hledání soubory .winmd.

## <a name="compiler-options"></a>Možnosti kompilátoru

|Možnost|Popis|
|------------|-----------------|
|[/ZW](../build/reference/zw-windows-runtime-compilation.md)<br /><br /> /ZW:nostdlib|Povolí jazyková rozšíření prostředí Windows Runtime.<br /><br /> `nostdlib` Parametr zabrání kompilátoru pomocí standardní předdefinované vyhledávací cesty k vyhledání souborů sestavení a .winmd.<br /><br /> **/ZW** – možnost kompilátoru implicitně určuje následující možnosti kompilátoru:<br /><br />- **/Fi** vccorlib.h, která vynutí zahrnutí souboru záhlaví vccorlib.h, který definuje mnoho typů, které jsou vyžadované kompilátor.<br />- [/FU](../build/reference/fu-name-forced-hash-using-file.md) Windows.winmd, která vynutí zahrnutí soubor Windows.winmd metadat, který je k dispozici v operačním systému a definuje mnoho typů v modulu Windows Runtime.<br />- **/FU** Platform.winmd, která vynutí zahrnutí Platform.winmd metadata souboru, který je poskytován kompilátorem a definuje většinu typů řady platformy oborů názvů.|
|[/AI](../build/reference/ai-specify-metadata-directories.md) *dir*|Přidá adresář, který je určený *dir* parametr do cesty pro hledání, kterou kompilátor používá k vyhledání souborů sestavení a .winmd.|
|**/FU**  *souboru*|Vynutí zahrnutí zadaném modulu nebo souboru .winmd. To znamená, není nutné zadat `#using` *souboru* ve zdrojovém kódu. Kompilátor automaticky vynutí zahrnutí svůj vlastní soubor Windows metadata, Platform.winmd.|
|/D "WINAPI_FAMILY = 2"|Vytvoří definici, která umožňuje používat podmnožinu Win32 SDK, která je kompatibilní s modulem Windows Runtime.|

## <a name="linker-options"></a>Možnosti linkeru

|Možnost|Popis|
|------------|-----------------|
|/ APPCONTAINER [: NO]|Označí spustitelný soubor jako spustitelný v kontejneru appcontainer (jenom).|
|/WINMD[:{NO&#124;ONLY}]|Generuje soubor .winmd a přidružený binární soubor. Tato možnost musí být předán linkeru pro .winmd, aby byly vypuštěny.<br /><br /> **Ne**– nebude generovat soubor winmd, ale generování binárního souboru.<br /><br /> **POUZE**– generuje soubor winmd, ale nebude generovat binárního souboru.|
|/ WINMDFILE:*název souboru*|Název souboru .winmd vygenerovat, namísto výchozí název souboru .winmd. Pokud více názvů souborů jsou zadané na příkazovém řádku, použije se poslední název.|
|/ WINMDDELAYSIGN SOUBORU [: NO]|Částečně podepíše soubor winmd a umístí veřejný klíč v binárním souboru.<br /><br /> **Ne**—(Default) nebude podepsání souboru winmd.<br /><br /> / Winmddelaysign souboru nemá žádný vliv, pokud je také zadán /WINMDKEYFILE nebo /WINMDKEYCONTAINER.|
|/ WINMDKEYCONTAINER:*název*|Určuje klíčový kontejner k podepsání sestavení. *Název* parametr odpovídá kontejneru klíčů, který se používá k podepsání souboru metadat.|
|/ WINMDKEYFILE:*název souboru*|Určuje klíč nebo dvojici klíčů k podepsání sestavení. *Filename* parametr odpovídá klíč, který se používá k podepsání souboru metadat.|

### <a name="remarks"></a>Poznámky

Při použití **/ZW**, kompilátor automaticky propojí verzi knihovny DLL z modulu Runtime jazyka C (CRT). Odkazování na statickou knihovnu verze není povolen, a veškeré jeho používání funkce CRT, které nejsou povoleny v aplikaci pro univerzální platformu Windows způsobí chybu kompilace.

## <a name="see-also"></a>Viz také

[Vytváření aplikací a knihoven](../cppcx/building-apps-and-libraries-c-cx.md)