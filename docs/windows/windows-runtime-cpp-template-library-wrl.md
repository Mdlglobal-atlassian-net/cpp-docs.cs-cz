---
title: "Knihovna šablon C++ prostředí Windows Runtime (WRL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
caps.latest.revision: "32"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a37b20af7ee9ef43c64fc0df24b47a380000eb6b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="windows-runtime-c-template-library-wrl"></a>Knihovna šablon C++ prostředí Windows Runtime (WRL)
Windows Runtime C++ šablony knihovny (WRL) je knihovna šablon, který poskytuje nízké úrovně způsob vytváření a používání komponent prostředí Windows Runtime.  
  
## <a name="benefits"></a>Výhody  
 Knihovna šablon C++ Runtime Windows umožňuje snadno implementovat a využívat komponenty modelu COM (Component Object). Poskytuje housekeeping techniky jako referenční počítání dobu trvání objektů a testování `HRESULT` hodnoty určující, zda operace byla úspěšná nebo neúspěšná. Úspěšně používat knihovna šablon C++ Runtime Windows, musíte pečlivě postupujte podle těchto pravidel a techniky.  
  
 C + +/ CX je nejdůležitější, na základě jazyka způsob, jak používat prostředí Windows Runtime komponenty. Knihovna šablon C++ prostředí Windows Runtime i C + +/ CX zjednodušit psaní kódu pro prostředí Windows Runtime automaticky provedením úloh housekeeping vaším jménem.  
  
 Knihovna šablon C++ prostředí Windows Runtime a C + +/ CX poskytovat různé výhody. Zde jsou některé důvody, které můžete chtít použít knihovna šablon C++ Runtime Windows místo C + +/ CX:  
  
-   Knihovna šablon C++ prostředí Windows Runtime přidá málo abstrakci přes Windows Runtime aplikace binární rozhraní (ABI), která poskytuje možnost řídit kódu pro lepší vytvořit nebo využívají rozhraní API systému Windows Runtime.  
  
-   C + +/ CX představuje COM `HRESULT` hodnoty jako výjimky. Pokud jste zděděn základu kódu, pomocí modelu COM nebo ten, který nepoužívá výjimky, můžete zjistit, že je knihovna šablon C++ Runtime Windows přirozenější způsob, jak pracovat s prostředí Windows Runtime, protože nemusíte používat výjimky.  
  
    > [!NOTE]
    >  Knihovna šablon C++ Runtime Windows používá `HRESULT` hodnoty a nevyvolá výjimku výjimky. Kromě toho knihovna šablon C++ Runtime Windows používá chytré ukazatele a vzoru RAII k zajištění objekty jsou při kódu aplikace vyvolá výjimku zničen správně. Další informace o chytré ukazatele a RAII najdete v tématu [chytré ukazatele](../cpp/smart-pointers-modern-cpp.md) a [objekty vlastní prostředky (RAII)](../cpp/objects-own-resources-raii.md).  
  
-   Účel a návrhu knihovna šablon C++ Runtime Windows se daly podnět pomocí ATL Active Template Library (), což je sada na základě šablon C++ tříd, které zjednodušují programování objektů COM. Vzhledem k tomu, že knihovna šablon C++ prostředí Windows Runtime používá standardní C++ zabalit prostředí Windows Runtime, můžete snadno portu a pracovat s mnoha existující komponenty modelu COM v ATL zapsána do prostředí Windows Runtime. Pokud už znáte ATL, můžete zjistit, že je knihovna šablon C++ prostředí Windows Runtime programování jednodušší.  
  
## <a name="getting-started"></a>Začínáme  
 Tady jsou některé prostředky, které vám může pomoct získat práce knihovna šablon C++ Runtime Windows hned.  
  
 [Knihovna Windows Runtime (WRL)](http://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)  
 V tomto videu Channel 9 Další informace o tom, jak vám může pomoci knihovna šablon C++ Runtime Windows zápisu aplikace pro univerzální platformu Windows a jak vytvářet a využívat komponenty prostředí Windows Runtime.  
  
 [Postupy: Aktivace a používání komponent prostředí Windows Runtime](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)  
 Ukazuje, jak používat knihovna šablon C++ Runtime Windows k inicializaci prostředí Windows Runtime a aktivace a používání komponent prostředí Windows Runtime.  
  
 [Postupy: dokončení asynchronních operací](../windows/how-to-complete-asynchronous-operations-using-wrl.md)  
 Ukazuje, jak pomocí knihovny šablon jazyka C++ Runtime Windows spouštět asynchronní operace a práci při dokončení operace.  
  
 [Postupy: zpracování událostí](../windows/how-to-handle-events-using-wrl.md)  
 Ukazuje, jak používat k přihlášení k odběru a zpracování událostí objektu prostředí Windows Runtime knihovna šablon C++ Runtime systému Windows.  
  
 [Návod: Vytvoření komponenty základní služby Windows Runtime](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md)  
 Ukazuje, jak vytvořit základní komponenty prostředí Windows Runtime, která sečte dvě čísla pomocí knihovny šablon jazyka C++ Runtime systému Windows. Také ukazuje, jak aktivovat události a používání komponent z aplikace univerzální platformu Windows, která používá jazyk JavaScript.  
  
 [Návod: Vytvoření aplikace pro Windows Store pomocí knihovny WRL a platformy Media Foundation](../windows/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)  
 Zjistěte, jak vytvořit aplikaci pro univerzální platformu Windows, která používá [Microsoft Media Foundation](http://msdn.microsoft.com/library/windows/apps/ms694197).  
  
 [Postupy: vytvoření klasické komponenty COM](../windows/how-to-create-a-classic-com-component-using-wrl.md)  
 Ukazuje, jak použít knihovna šablon C++ Runtime Windows k vytvoření základní komponenty modelu COM a základní způsob, jak zaregistrovat a využívat komponenty modelu COM z aplikace na ploše.  
  
 [Postupy: vytváření instancí komponent knihovny WRL přímo](../windows/how-to-instantiate-wrl-components-directly.md)  
 Další informace o použití [Microsoft::WRL::Make](../windows/make-function.md) a [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) funkce pro vytvoření instance součásti z modulu, který ji definuje.  
  
 [Postupy: vytváření souborů .h z metadat windows pomocí winmdidl.exe a midlrt.exe](../windows/use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)  
 Ukazuje, jak používat vlastní komponenty prostředí Windows Runtime z knihovny WRL vytvořením souboru IDL z .winmd metadat.  
  
 [Návod: Připojení pomocí úloh a žádostí XML HTTP](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 Ukazuje, jak používat [IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908) a [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71) rozhraní společně s úkoly na odesílání žádostí HTTP GET a POST na webovou službu v aplikaci pro univerzální platformu Windows.  
  
 [Ukázka Optimalizátor cestě Bing Maps](http://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)  
 Používá `HttpRequest` třídu, která je definována v [návod: připojení pomocí úloh a žádostí XML HTTP](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) v kontextu kompletní aplikace pro univerzální platformu Windows.  
  
 [Vytvoření komponenty prostředí Windows Runtime DLL s ukázkou C++](http://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)  
 Ukazuje, jak používat knihovna šablon C++ Runtime Windows vytvořit komponentu knihovny DLL v procesu a využívat z C + +/ CX, JavaScript a C#.  
  
 [Ukázka hry mramor bludiště DirectX](http://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)  
 Ukazuje, jak používat ke správě životnost COM – součásti například DirectX a Media Foundation v rámci dokončení 3D herní knihovna šablon C++ Runtime systému Windows.  
  
 [Odesílání oznámení informační zprávy z ukázkové aplikace klasické pracovní plochy](http://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)  
 Demonstruje použití knihovny šablon jazyka C++ Runtime Windows pro práci s informační zprávou oznámení z aplikace na ploše.  
  
## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Knihovna šablon C++ prostředí Windows Runtime ve srovnání s ATL  
 Vzhledem k tomu slouží k vytvoření malého, rychlé objekty modelu COM se podobá knihovna šablon C++ prostředí Windows Runtime Active šablony Library (ATL). Knihovna šablon C++ prostředí Windows Runtime a knihovna ATL také sdílet koncepty, jako je například definice objektů v modulech explicitní registrační rozhraní a otevřete vytváření objektů s použitím objektů Factory. Knihovna šablon C++ prostředí Windows Runtime celý může být, pokud jste obeznámeni s ATL.  
  
 Knihovna šablon C++ prostředí Windows Runtime podporuje funkce COM, která je požadována pro univerzální platformu Windows aplikace. Proto se liší od knihovny ATL vzhledem k tomu vynechán přímé podpory pro funkce COM, jako:  
  
-   Agregace  
  
-   uložené implementace  
  
-   duální rozhraní (`IDispatch`)  
  
-   rozhraní pro standardní výčty  
  
-   body připojení  
  
-   Úplné vypnutí rozhraní  
  
-   Vložení OLE  
  
-   ActiveX – ovládací prvky  
  
-   Model COM+  
  
## <a name="concepts"></a>Koncepty  
 Knihovna šablon C++ prostředí Windows Runtime obsahuje typy, které představují několik základní koncepty. Následující části popisují tyto typy.  
  
### <a name="comptr"></a>ComPtr  
 [ComPtr](../windows/comptr-class.md) je *chytré ukazatele* typ, který představuje rozhraní, která je zadána parametr šablony. Použití `ComPtr` deklarovat proměnnou a tu můžete přístup ke členům v objektu, který je odvozený z rozhraní. `ComPtr`automaticky udržuje počet odkazů pro základní ukazatel rozhraní a uvolní rozhraní, kdy přestane počet odkazů na nulu.  
  
### <a name="runtimeclass"></a>RuntimeClass  
 [RuntimeClass](../windows/runtimeclass-class.md) představuje instancí třídu, která dědí sada zadaný rozhraní. A `RuntimeClass` objekt můžete poskytovat kombinaci podpory pro jeden nebo více rozhraní Windows Runtime COM nebo slabé odkaz na komponentu.  
  
### <a name="module"></a>Modul  
 [Modul](../windows/module-class.md) představuje kolekci související objekty. A `Module` spravuje objekt pro vytváření tříd, které pak vytvoří objekty a registrace, který umožňuje jiné aplikace použít objekt.  
  
### <a name="callback"></a>Zpětné volání  
 [Zpětného volání](../windows/callback-function-windows-runtime-cpp-template-library.md) funkce vytvoří objekt, jehož členská funkce je obslužné rutiny události (metody zpětného volání). Použití `Callback` funkce zápis asynchronní operace.  
  
### <a name="eventsource"></a>EventSource  
 [EventSource](../windows/eventsource-class.md) slouží ke správě *delegovat* obslužné rutiny událostí. Knihovna šablon C++ prostředí Windows Runtime použít k implementaci delegáta a použití `EventSource` Pokud chcete přidat, odebrat a vyvolání delegáti.  
  
### <a name="asyncbase"></a>AsyncBase  
 [AsyncBase](../windows/asyncbase-class.md) poskytuje virtuální metody, které představují asynchronní programovací model Windows Runtime. Přepsání členů v této třídy pro vytvoření vlastní třídy, které můžete spustit, zastavit nebo průběh asynchronní operace.  
  
### <a name="ftmbase"></a>FtmBase  
 [FtmBase](../windows/ftmbase-class.md) představuje volné zařazování vláken objektu. `FtmBase`vytvoří tabulku globální rozhraní (GIT) a pomáhá spravovat objekty zařazování a proxy serveru.  
  
### <a name="weakref"></a>WeakRef  
 [WeakRef](../windows/weakref-class.md) je typ čipové ukazatele, který reprezentuje *slabé odkaz*, který odkazuje na objekt, který může nebo nemusí být dostupné. A `WeakRef` objekt lze použít pouze prostředí Windows Runtime a ne klasického modelu COM.  
  
 A `WeakRef` objekt obvykle představuje objekt, jehož existence řídí na externí vlákna nebo aplikaci. Například `WeakRef` objekt může odkazovat na objekt souboru. Když je soubor otevřený `WeakRef` je platný a je přístupný odkazovaný soubor. Ale při zavření souboru, `WeakRef` je neplatný a soubor není přístupný.  
  
## <a name="related-topics"></a>Související témata  
  
|||  
|-|-|  
|[Šablona projektu knihovny tříd](../windows/wrl-class-library-project-template.md)|Popisuje, jak pro přístup k šabloně projektu knihovny tříd WRL. Tato šablona pomáhá zjednodušit pomocí sady Visual Studio k vytvoření komponentů prostředí Windows Runtime.|  
|[Klíč rozhraní API podle kategorie](../windows/key-wrl-apis-by-category.md)|Označuje primární typy knihovna šablon C++ prostředí Windows Runtime, funkcemi a makry.|  
|[Referenční dokumentace](../windows/wrl-reference.md)|Obsahuje referenční informace pro knihovny šablon jazyka C++ Runtime systému Windows.|  
|[Stručná referenční dokumentace (prostředí Windows Runtime a Visual C++)](http://go.microsoft.com/fwlink/?LinkId=229180)|Stručně popisuje C + +/ CX funkce, které podporují prostředí Windows Runtime.|  
|[Pomocí modulu Runtime součásti systému Windows v jazyce Visual C++](http://go.microsoft.com/fwlink/?LinkId=229155)|Ukazuje, jak používat C + +/ CX pro vytvoření základní komponenty prostředí Windows Runtime.|