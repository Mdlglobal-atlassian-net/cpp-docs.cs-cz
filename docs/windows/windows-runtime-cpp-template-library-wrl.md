---
title: Knihovna šablon C++ prostředí Windows Runtime (WRL)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
ms.openlocfilehash: 777e8226a12b3e57c136ea54d301ff7c9eb890a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641932"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Knihovna šablon C++ prostředí Windows Runtime (WRL)

Windows Runtime C++ šablony knihovny (WRL) je knihovna šablon, která poskytuje nízké úrovně způsob vytváření a používání komponent prostředí Windows Runtime.

> [!NOTE]
> WRL je nyní nahrazena C + +/ WinRT, standard C ++ 17 jazyk projekci pro rozhraní API Windows Runtime. C + +/ WinRT je k dispozici v sadě SDK Windows 10 verze 1803 dále. C + +/ WinRT je implementované jenom v souborech hlaviček a navržená tak, aby poskytují přístup k prvotřídní moderní rozhraní Windows API.

> Pomocí C + +/ WinRT, můžete současně využívat a vytvářet rozhraní API Windows Runtime pomocí jakékoli standardům C ++ 17 kompilátoru. C + +/ WinRT obvykle vrací lepší výsledky a vytváří menší binárních souborů než jakékoli jiné možnosti jazyka prostředí Windows Runtime. Budeme dál podporovat C + +/ CX a WRL, ale důrazně doporučujeme, aby nové aplikace pomocí C + +/ WinRT. Další informace najdete v tématu [C + +/ WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index).

## <a name="benefits"></a>Výhody

Knihovna šablon C++ Windows Runtime umožňuje snadněji implementovat a používat komponenty modelu COM (Component Object). Poskytuje metody údržby pořádku jako počítání odkazů ke správě životnosti objektů a testování hodnoty HRESULT k určení, zda operace bylo úspěšné nebo neúspěšné. Pro úspěšné fungování knihovna šablon C++ Windows Runtime, je třeba pečlivě dodržovat tato pravidla a postupy.

C + +/ CX se vysoké úrovně, založený na jazyce způsob použití součásti prostředí Windows Runtime. Knihovna šablon C++ Runtime Windows i C + +/ CX zjednodušit psaní kódu pro Windows Runtime automatickým prováděním údržby pořádku za vás.

Knihovna šablon C++ Windows Runtime a C + +/ CX poskytují různé výhody. Tady jsou některé důvody může být vhodné nahrazujícím knihovna šablon C++ Windows Runtime jazyka C + +/ CX:

- Knihovna šablon C++ Runtime Windows přidá trochu abstrakce přes Windows Runtime aplikace binární rozhraní (ABI), získáte možnost ovládat základní kód pro lepší tvorbu nebo zpracování rozhraní API Windows Runtime.

- C + +/ CX představuje hodnoty HRESULT modelu COM jako výjimky. Jestliže jste zdědili základ kódu, který používá COM, nebo který výjimky nepoužívá, můžete zjistit, že knihovna šablon C++ Windows Runtime je přirozenější způsob, jak pracovat s modulem Windows Runtime, protože není nutné používat výjimky.

   > [!NOTE]
   > Knihovna šablon C++ Windows Runtime používá hodnoty HRESULT a nevyvolává výjimky. Kromě toho knihovna šablon C++ Windows Runtime používá inteligentní ukazatele a vzorek RAII, aby k zajištění, že objekty jsou správně zničeny, když kód aplikace vyvolá výjimku. Další informace o inteligentních ukazatelích a RAII naleznete v tématu [inteligentní ukazatele](../cpp/smart-pointers-modern-cpp.md) a [objekty vlastní prostředky (RAII)](../cpp/objects-own-resources-raii.md).

- Účel a návrh knihovna šablon C++ Windows Runtime inspirován podle aktivní šablony knihovny (ATL), což je sada šablonových tříd C++ a, které zjednodušují programování objektů modelu COM. Vzhledem k tomu, že knihovna šablon C++ Windows Runtime používá standardní C++ pro zalomení modulu Windows Runtime, můžete snadněji portovat a pracovat s mnoha stávající komponentami modelu COM v ATL do prostředí Windows Runtime. Pokud již znáte ATL, můžete zjistit, že je knihovna šablon C++ Windows Runtime programování jednodušší.

## <a name="getting-started"></a>Začínáme

Tady jsou některé prostředky, které můžete hned začít pracovat s knihovna šablon C++ Windows Runtime.

[Knihovna Windows Runtime (WRL)](https://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)<br/>
V tomto videu Channel 9 Další informace o tom, jak se knihovna šablon C++ Runtime Windows pomáhá zápisu aplikace univerzální platformy Windows (UPW) a jak vytvářet a využívat komponenty prostředí Windows Runtime.

[Postupy: Aktivace a používání komponent prostředí Windows Runtime](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)<br/>
Ukazuje, jak pomocí šablony knihovna Windows Runtime C++ inicializovat Windows Runtime a aktivaci a používání komponent prostředí Windows Runtime.

[Postupy: dokončení asynchronních operací](../windows/how-to-complete-asynchronous-operations-using-wrl.md)<br/>
Ukazuje způsob použití knihovny šablon jazyka C++ Runtime Windows ke spuštění asynchronních operací a provedení práce po dokončení operací.

[Postupy: zpracování událostí](../windows/how-to-handle-events-using-wrl.md)<br/>
Ukazuje způsob použití knihovny šablon jazyka C++ Runtime Windows přihlásit k odběru a zpracování událostí objekt prostředí Windows Runtime.

[Návod: Vytvoření aplikace pro UPW s použitím knihovny WRL a platformy Media Foundation](../windows/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)<br/>
Naučíte se vytvářet aplikace pro UPW, která používá [Microsoft Media Foundation](/windows/desktop/medfound/microsoft-media-foundation-sdk).

[Postupy: vytvoření klasické komponenty COM](../windows/how-to-create-a-classic-com-component-using-wrl.md)<br/>
Ukazuje, jak pomocí šablony knihovna Windows Runtime C++ k vytvoření základní komponenty modelu COM a základní způsob, jak zaregistrovat a využívat komponenty modelu COM z desktopové aplikace.

[Postupy: Přímé vytváření instancí komponent knihovny WRL](../windows/how-to-instantiate-wrl-components-directly.md)<br/>
Další informace o použití [Microsoft::WRL:: Make](../windows/make-function.md) a [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) pro vytvoření instance komponenty z modulu, který ji definuje.

[Postupy: Vytváření souborů .h z metadat Windows pomocí nástrojů winmdidl.exe a midlrt.exe](../windows/use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)<br/>
Ukazuje, jak využívat vlastní součásti prostředí Windows Runtime z WRL vytvořením souboru IDL z metadat .winmd.

[Návod: Připojení pomocí úloh a žádostí XML HTTP](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Ukazuje způsob použití [IXMLHTTPRequest2](/previous-versions/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2) a [IXMLHTTPRequest2Callback](/previous-versions/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2callback) spolu s úkoly odesílajícími požadavky HTTP GET a POST na webovou službu v aplikaci UWP.

[Příklad optimalizace cesty mapy Bing](https://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)<br/>
Používá `HttpRequest` třídu, která je definována v [návod: připojení pomocí úloh a žádostí XML HTTP](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) v souvislosti s kompletní aplikace pro UPW.

[Vytváření součásti modulu Windows Runtime s ukázkou jazyka C++](https://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)<br/>
Ukazuje, jak pomocí šablony knihovna Windows Runtime C++ vytvořit komponentu knihovny DLL v procesu a používat ji v jazyce C + +/ CX, JavaScriptu a C#.

[Ukázka hry mramorového bludiště DirectX](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)<br/>
Popisuje způsob použití knihovny šablon jazyka C++ Runtime Windows ke správě životnosti komponent modelu COM, jako je rozhraní DirectX a platformy Media Foundation v souvislosti s kompletní 3D hrou.

[Odesílání oznámení z ukázkové aplikace klasické pracovní plochy](https://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)<br/>
Popisuje způsob použití knihovny šablon jazyka C++ Runtime Windows pro práci s oznámeními pro oznámení z desktopové aplikace.

## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Knihovna šablon C++ prostředí Windows Runtime porovnané s ATL.

Knihovna šablon C++ Windows Runtime podobá aktivní šablony knihovny (ATL), protože slouží k vytvoření malé, rychlé objekty modelu COM. Knihovna šablon C++ Windows Runtime a knihovny ATL také sdílí koncepty, jako jsou definice objektů v modulech, explicitní registraci rozhraní a otevře vytváření objektů pomocí továren. Vyhovuje knihovna šablon C++ Windows Runtime může být, pokud jste obeznámeni s knihovnou ATL.

Knihovna šablon C++ Windows Runtime podporuje funkce modelu COM, která je požadována pro aplikace pro UPW. Proto se liší od knihovny ATL protože vynechá přímou podporu funkcí modelu COM, jako:

- Agregace

- uložené implementace

- duální rozhraní (`IDispatch`)

- standardní rozhraní čítače

- body připojení

- odtržených rozhraní

- Vložení OLE

- ActiveX – ovládací prvky

- Model COM+

## <a name="concepts"></a>Koncepty

Knihovna šablon C++ Windows Runtime poskytuje typy, které představují několik základních pojmů. Následující části popisují tyto typy.

### <a name="comptr"></a>ComPtr

[ComPtr](../windows/comptr-class.md) je *inteligentního ukazatele* typ, který představuje rozhraní, které je určeno parametrem šablony. Použití `ComPtr` k deklaraci proměnné, které můžete přístup ke členům v objektu, který je odvozen z rozhraní. `ComPtr` automaticky udržuje počet odkazů pro základního ukazatele rozhraní a uvolní rozhraní, když počet odkazů dosáhne nuly.

### <a name="runtimeclass"></a>RuntimeClass

[RuntimeClass](../windows/runtimeclass-class.md) představuje instance třídy, která dědí sadu zadaných rozhraní. A `RuntimeClass` objektu můžete poskytovat kombinaci podpory pro jedno nebo více rozhraní Windows Runtime COM nebo Slabý odkaz na komponentu.

### <a name="module"></a>Modul

[Modul](../windows/module-class.md) představuje kolekci souvisejících objektů. A `Module` objektu spravuje vytváření tříd, které vytvářejí objekty a registraci, což umožňuje jiným aplikacím použít objekt.

### <a name="callback"></a>zpětné volání

[Zpětného volání](../windows/callback-function-windows-runtime-cpp-template-library.md) funkce vytvoří objekt, jehož členská funkce je obslužnou rutinu události (metoda zpětného volání). Použití `Callback` funkce zapište asynchronní operace.

### <a name="eventsource"></a>EventSource

[EventSource](../windows/eventsource-class.md) slouží ke správě *delegovat* obslužných rutin událostí. Použití knihovny šablon jazyka C++ Windows Runtime delegáta implementujete a pomocí `EventSource` Pokud chcete přidat, odebrat nebo vyvoláte.

### <a name="asyncbase"></a>AsyncBase

[Asyncbase –](../windows/asyncbase-class.md) poskytuje virtuální metody, které představují asynchronní programovací model Windows Runtime. Přepište členy této třídy pro vytvoření vlastní třídy, které můžete spustit, zastavit nebo zkontrolovat průběh asynchronní operace.

### <a name="ftmbase"></a>FtmBase

[Ftmbase –](../windows/ftmbase-class.md) představuje objekt s volným zařazováním vláken. `FtmBase` vytvoří globální tabulku rozhraní (GIT) a pomáhá spravovat objekty zařazování a proxy.

### <a name="weakref"></a>WeakRef

[Weakref –](../windows/weakref-class.md) je typ inteligentního ukazatele, který představuje *nestálý odkaz*, které se odkazuje na objekt, který může nebo nemusí být dostupný. A `WeakRef` objekt lze použít pouze modul runtime pro Windows a nikoli podle klasického modelu COM.

A `WeakRef` objekt obvykle představuje objekt, jehož existence je řízena vnějším vláknem nebo aplikací. Například `WeakRef` objekt může odkazovat na objekt v souboru. Když je soubor otevřen, `WeakRef` platné a odkazovaný soubor je přístupný. Ale při zavření souboru je `WeakRef` není platný a soubor není přístupný.

## <a name="related-topics"></a>Související témata

|||
|-|-|
|[Nejdůležitější rozhraní API podle kategorie](../windows/key-wrl-apis-by-category.md)|Zvýrazní primární typy knihovna šablon C++ Windows Runtime, funkcemi a makry.|
|[Referenční informace](../windows/wrl-reference.md)|Obsahuje referenční informace pro knihovna šablon C++ Windows Runtime.|
|[Stručná referenční příručka (Windows Runtime a Visual C++)](../cppcx/quick-reference-c-cx.md)|Stručně popisuje C + +/ CX funkce, které podporují prostředí Windows Runtime.|
|[Použití součástí prostředí Windows Runtime v jazyce Visual C++](/windows/uwp/winrt-components/walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp)|Ukazuje, jak použít C + +/ CX pro vytvoření základní komponenty prostředí Windows Runtime.|
