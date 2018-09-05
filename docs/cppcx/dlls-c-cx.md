---
title: Knihovny DLL (C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/06/2018
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ac06336e5ba80406157285ebe660080aff6e319
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763630"
---
# <a name="dlls-ccx"></a>DLLs (C++/CX)

Visual Studio můžete použít k vytvoření standardním Win32 DLL nebo součásti prostředí Windows Runtime knihovny DLL, která mohou být spotřebovány aplikací univerzální platformy Windows (UPW). Standardní knihovny DLL, který byl vytvořen pomocí verze sady Visual Studio nebo kompilátor Visual C++, která je starší než Visual Studio 2012 v aplikace pro UPW nemusí načíst správně a nemusí předat ověřovací test aplikace v Microsoft Store.

## <a name="windows-runtime-component-dlls"></a>Součást prostředí Windows Runtime knihovny DLL

V téměř všech případech Pokud chcete vytvořit knihovnu DLL pro použití v aplikaci UWP, vytvořte ho jako součást prostředí Windows Runtime pomocí šablony projektu s tímto názvem. Vytvoření projektu součásti prostředí Windows Runtime pro knihovny DLL, které mají veřejné nebo privátní typy Windows Runtime. Součást prostředí Windows Runtime je přístupná z aplikací, které jsou napsané v libovolném jazyce kompatibilního s Windows Runtime. Ve výchozím nastavení kompilátoru pro součást prostředí Windows Runtime projektu použijte **/ZW** přepnout. Soubor .winmd musí mít stejný název, který má kořenový obor názvů. Například třída, která má název A.B.C.MyClass dá vytvořit instance pouze v případě, že je definována v souboru metadat, který je pojmenován A.winmd a A.B.winmd nebo A.B.C.winmd. Název knihovny DLL nemusí odpovídat názvu souboru .winmd.

Další informace najdete v tématu [vytváření komponent Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>Chcete-li odkazovat na součást prostředí Windows Runtime třetích stran binární ve vašem projektu

1. Otevřete místní nabídku pro projekt, který bude používat knihovny DLL a klikněte na tlačítko **vlastnosti**. Na **společné vlastnosti** zvolte **přidat nový odkaz** tlačítko.

1. Součást prostředí Windows Runtime se skládá z soubor DLL a soubor .winmd obsahující metadata. Tyto soubory jsou obvykle umístěny ve stejné složce. V levém podokně **přidat odkaz** dialogového okna zvolte **Procházet** tlačítko a pak přejděte do umístění knihovny DLL a jeho soubor winmd. Další informace najdete v tématu [sady SDK rozšíření](/visualstudio/extensibility/creating-a-software-development-kit#ExtensionSDKs).

## <a name="standard-dlls"></a>Standardní knihovny DLL

Můžete vytvořit standardní knihovny DLL pro kód jazyka C++, který nebude využívat nebo vytvářet veřejné typy Windows Runtime a využívat z aplikace pro UPW. Typ projektu dynamické knihovny (DLL) použijte, pokud chcete migrovat existující knihovny DLL pro kompilaci v této verzi sady Visual Studio, ale kód nejde převést na projekt pro součást prostředí Windows Runtime. Při použití následujících kroků, knihovny DLL se nasadí společně s vaší aplikace v balíčku .appx spustitelný soubor.

### <a name="to-create-a-standard-dll-in-visual-studio"></a>Chcete-li vytvořit standardní knihovny DLL v sadě Visual Studio

1. V panelu nabídky zvolte **souboru**, **nový**, **projektu**a pak vyberte **dynamické propojení knihovna (DLL)** šablony.

1. Zadejte název projektu a klikněte na tlačítko **OK** tlačítko.

1. Přidejte kód. Nezapomeňte použít `__declspec(dllexport)` pro funkce, které máte v úmyslu export – například `__declspec(dllexport) Add(int I, in j);`

1. Přidat `#include winapifamily.h` zahrnout tento soubor hlavičky ze sady Windows SDK pro aplikace pro UPW a nastavte makro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>Chcete-li odkazovat standardní projektu knihovny DLL ve stejném řešení

1. Otevřete místní nabídku pro projekt, který bude používat knihovny DLL a klikněte na tlačítko **vlastnosti**. Na **společné vlastnosti** zvolte **přidat nový odkaz** tlačítko.

1. V levém podokně vyberte **řešení**a potom v pravém podokně vyberte příslušné políčko.

1. Soubory zdrojového kódu, přidejte `#include` – příkaz souboru hlaviček knihovny DLL, podle potřeby.

### <a name="to-reference-a-standard-dll-binary"></a>Chcete-li odkazovat standardní binární soubor knihovny DLL

1. Zkopírujte soubor knihovny DLL, .lib soubor a soubor hlaviček a vložte je do vhodného umístění, například v aktuální složce projektu.

1. Otevřete místní nabídku pro projekt, který bude používat knihovny DLL a klikněte na tlačítko **vlastnosti**. Na **vlastnosti konfigurace**, **Linkeru**, **vstup** stránce, přidejte soubor .lib jako závislost.

1. Soubory zdrojového kódu, přidejte `#include` – příkaz souboru hlaviček knihovny DLL, podle potřeby.

### <a name="to-migrate-an-existing-win32-dll-for-uwp-app-compatibility"></a>K migraci existujícího Win32 DLL z důvodu kompatibility aplikace UPW

1. Vytvořte projekt typu knihovny DLL (Universal Windows) a přidejte do ní existující zdrojový kód.

1. Přidat `#include winapifamily.h` zahrnout tento soubor hlavičky ze sady Windows SDK pro aplikace pro UPW a nastavte makro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

1. Soubory zdrojového kódu, přidejte `#include` – příkaz souboru hlaviček knihovny DLL, podle potřeby.
