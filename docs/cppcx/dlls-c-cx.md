---
title: Knihovny DLL (C + +/ CX) | Microsoft Docs
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
caps.latest.revision: "21"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: a3202ba5bd5b42b3f4853348258d5c4e3e5a2072
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dlls-ccx"></a>Knihovny DLL (C + +/ CX)
Visual Studio můžete použít k vytvoření standardní knihovny DLL Win32 nebo prostředí Windows Runtime součást knihovnu DLL, kterou mohou být spotřebovávána aplikace pro univerzální platformu Windows. Standardní knihovny DLL, která byla vytvořena pomocí verze sady Visual Studio nebo – kompilátor Visual C++, která je starší než Visual Studio 2012 nemusí načíst správně v aplikaci pro univerzální platformu Windows a nemusí projde testem ověření aplikace v [!INCLUDE[win8_appstore_long](../cppcx/includes/win8-appstore-long-md.md)].  
  
## <a name="windows-runtime-component-dlls"></a>Knihovny DLL komponenty prostředí Windows Runtime  
 Ve většině případů Pokud chcete vytvořit knihovnu DLL pro použití v aplikaci pro univerzální platformu Windows, vytvořte ho jako součást prostředí Windows Runtime pomocí šablony projektu s tímto názvem. Můžete vytvořit projekt komponenty prostředí Windows Runtime pro knihovny DLL, které mají veřejných nebo privátních typy prostředí Windows Runtime. Komponent prostředí Windows Runtime jsou přístupné z aplikací, které jsou napsané v libovolném jazyce kompatibilní se systémem Windows Runtime. Ve výchozím nastavení kompilátoru pro prostředí Windows Runtime součást projektu pomocí **/ZW** přepínače. Soubor .winmd musí mít stejný název, který má kořenového oboru názvů. Například třídu, která je s názvem A.B.C.MyClass se dá vytvořit instance pouze v případě, že je definována v souboru metadat, který je pojmenován A.winmd nebo A.B.winmd nebo A.B.C.winmd. Název knihovny DLL nemusí odpovídat názvu souboru .winmd.  
  
 Další informace najdete v tématu [vytváření součásti systému Windows Runtime v jazyce C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md).  
  
#### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>Chcete-li prostředí Windows Runtime součást třetích stran binární ve vašem projektu  
  
1.  Otevřete místní nabídku pro projekt, který bude používat knihovnu DLL a potom zvolte **vlastnosti**. Na **společných vlastností** vyberte **přidat nový odkaz** tlačítko.  
  
2.  Komponent prostředí Windows Runtime se skládá z .winmd soubor, který obsahuje metadata souboru DLL. Obvykle se tyto soubory jsou umístěny ve stejné složce. V levém podokně **přidat odkaz na** dialogovém okně vyberte **Procházet** tlačítko a pak přejděte do umístění knihovny DLL a jeho .winmd souboru. Další informace najdete v tématu [kurz: vytvoření a používání rozšíření sady SDK](http://msdn.microsoft.com/en-us/001e2fca-3d56-43ab-a5e0-0561d085679f).  
  
## <a name="standard-dlls"></a>Standardní knihovny DLL  
 Můžete vytvořit standardní knihovny DLL pro kód C++, která se využívají nebo vytvořit veřejné typy prostředí Windows Runtime a využívat z aplikace pro univerzální platformu Windows. Typ projektu Universal Windows Platform DLL použijte, pokud chcete migrovat existující knihovny DLL kompilovat v této verzi sady Visual Studio, ale není převést kód do projektu komponenty prostředí Windows Runtime. Použijete-li následující kroky, nasadí se společně se vaše aplikace spustitelného souboru v balíčku .appx knihovnu DLL.  
  
#### <a name="to-create-a-standard-dll-in-visual-studio"></a>Chcete-li vytvořit standardní knihovny DLL v sadě Visual Studio  
  
1.  Na řádku nabídek zvolte **soubor**, **nový**, **projektu**a potom vyberte šablonu, Universal Windows Platform DLL.  
  
2.  Zadejte název projektu a zvolte **OK** tlačítko.  
  
3.  Přidejte kód. Nezapomeňte použít `__declspec(dllexport)` pro funkce, které chcete exportovat – například`__declspec(dllexport) Add(int I, in j);`  
  
4.  Přidat `#include winapifamily.h` zahrnout tento soubor hlaviček ze sady Windows SDK pro aplikace pro univerzální platformu Windows a nastavte makro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.  
  
#### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>Chcete-li ze stejného řešení standardní projektu knihovny DLL  
  
1.  Otevřete místní nabídku pro projekt, který bude používat knihovnu DLL a potom zvolte **vlastnosti**. Na **společných vlastností** vyberte **přidat nový odkaz** tlačítko.  
  
2.  V levém podokně vyberte **řešení**a pak v pravém podokně vyberte příslušné políčko.  
  
3.  Vaše soubory zdrojového kódu přidat `#include` příkaz pro hlavičkový soubor knihovny DLL, podle potřeby.  
  
#### <a name="to-reference-a-standard-dll-binary"></a>Chcete-li standardní binární soubor knihovny DLL  
  
1.  Zkopírujte soubor knihovny DLL, .lib soubor a soubor hlaviček a vložte je do vhodného umístění – například v aktuální složce projektu.  
  
2.  Otevřete místní nabídku pro projekt, který bude používat knihovnu DLL a potom zvolte **vlastnosti**. Na **vlastnosti konfigurace**, **Linkeru**, **vstup** stránky, přidejte soubor .lib jako závislost.  
  
3.  Vaše soubory zdrojového kódu přidat `#include` příkaz pro hlavičkový soubor knihovny DLL, podle potřeby.  
  
#### <a name="to-migrate-an-existing-win32-dll-for-universal-windows-platform-app-compatibility"></a>K migraci existujících Win32 knihovny DLL pro univerzální platformu Windows kompatibility aplikace  
  
1.  Vytvoření projektu typu Universal Windows Platform DLL a do ní přidejte existujícím zdrojovém kódu.  
  
2.  Přidat `#include winapifamily.h` zahrnout tento soubor hlaviček ze sady Windows SDK pro aplikace pro univerzální platformu Windows a nastavte makro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.  
  
3.  Vaše soubory zdrojového kódu přidat `#include` příkaz pro hlavičkový soubor knihovny DLL, podle potřeby.  
  
