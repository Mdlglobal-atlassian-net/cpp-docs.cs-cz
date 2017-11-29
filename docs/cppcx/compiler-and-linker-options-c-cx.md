---
title: "Možnosti kompilátoru a Linkeru (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecfadce8-3a3f-40cc-bb01-b4731f8d2fcb
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 868e167e68cf2fba6a8252ba390ab73268a78005
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-and-linker-options-ccx"></a>Možnosti kompilátoru a Linkeru (C + +/ CX)
Proměnné prostředí, C + +/ CX – možnosti kompilátoru a linkeru možnosti podporují vytváření aplikací pro prostředí Windows Runtime.  
  
## <a name="library-path"></a>Cesta ke knihovně  
 Proměnná prostředí % LIBPATH % Určuje výchozí cestu k vyhledání .winmd soubory.  
  
## <a name="compiler-options"></a>Možnosti kompilátoru  
  
|Možnost|Popis|  
|------------|-----------------|  
|[/ZW](../build/reference/zw-windows-runtime-compilation.md)<br /><br /> /ZW:nostdlib|Umožňuje prostředí Windows Runtime jazyková rozšíření.<br /><br /> `nostdlib` Parametr zabrání kompilátoru pomocí cesty standardní, předdefinované vyhledávání nalézt sestavení a .winmd soubory.<br /><br /> **/ZW** – možnost kompilátoru implicitně určuje následující možnosti kompilátoru:<br /><br /> -   **/Fi** vccorlib.h, který vynutí zahrnutí vccorlib.h soubor hlaviček, který definuje mnoho typů, které vyžaduje kompilátor.<br />-   [/FU](../build/reference/fu-name-forced-hash-using-file.md) Windows.winmd, který vynutí zahrnutí Windows.winmd metadata souboru, který je k dispozici v operačním systému a definuje mnoho typů v prostředí Windows Runtime.<br />-   **/FU** Platform.winmd, který vynutí zahrnutí Platform.winmd metadata souboru, který zajišťuje kompilátor a definuje většinu typů řady platformy oborů názvů.|  
|[/AI](../build/reference/ai-specify-metadata-directories.md) *dir*|Přidá adresář, který je určený *dir* parametr vyhledávání cestu, která kompilátor používá k nalezení sestavení a .winmd soubory.|  
|**/FU***souboru* |Vynutí zahrnutí zadaném modulu nebo .winmd souboru. To znamená, nemusíte určit `#using` *souboru* ve zdrojovém kódu. Kompilátor automaticky vynutí zahrnutí vlastního Windows metadata souboru Platform.winmd.|  
|/D "WINAPI_FAMILY = 2"|Vytvoří definici, která umožňuje použití podmnožinu Win32 SDK, který je kompatibilní s prostředí Windows Runtime.|  
  
## <a name="linker-options"></a>Možnosti linkeru  
  
|Možnost|Popis|  
|------------|-----------------|  
|/ APPCONTAINER [: NE]|Označí tento spustitelný soubor jako spustitelného v kontejneru appcontainer (pouze).|  
|/ WINMD [: {Č &#124; POUZE}]|Vysílá soubor .winmd a přidružený binární soubor. Tuto možnost, musí být předán linkeru pro .winmd pro vypuštění.<br /><br /> **Ne**– není emitování soubor .winmd, ale emitování binární soubor.<br /><br /> **POUZE**– vysílá soubor .winmd, ale není emitování binární soubor.|  
|/ WINMDFILE:*filename*|Název souboru .winmd pro vydávání místo výchozí název souboru .winmd. Pokud více názvů souborů jsou nastaveny na příkazovém řádku, použije se příjmení.|  
|/ WINMDDELAYSIGN [: NE]|Částečně podepíše soubor .winmd a umístí veřejný klíč do binárního souboru.<br /><br /> **Ne**—(Default) není podepsání souboru .winmd.<br /><br /> / WINMDDELAYSIGN nemá žádný vliv, pokud /WINMDKEYFILE nebo /WINMDKEYCONTAINER rovněž je zadán.|  
|/ WINMDKEYCONTAINER:*název*|Určuje kontejner klíčů pro podepsání sestavení. *Název* parametr odpovídá kontejneru klíčů, který se používá k podepsání souboru metadat.|  
|/ WINMDFILE:*filename*|Určuje klíč nebo pár klíčů k podepsání sestavení. *Filename* parametr odpovídá klíč, který se používá k podepsání souboru metadat.|  
  
### <a name="remarks"></a>Poznámky  
 Při použití **/ZW**, kompilátor automaticky odkazuje na knihovnu DLL verze z modulu Runtime jazyka C (CRT). Propojení na verzi statické knihovny není povolen a jakékoli použití funkcí CRT, které nejsou povoleny v aplikaci pro univerzální platformu Windows může způsobit chyby kompilace.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření aplikací a knihovny](../cppcx/building-apps-and-libraries-c-cx.md)