---
title: Knihovna šablon C++ prostředí Windows Runtime (WRL)
ms.date: 11/04/2016
ms.topic: landing-page
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
ms.openlocfilehash: 7a92676d198ed9ddffeae9a834ebd358c2c58e90
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740834"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Knihovna šablon C++ prostředí Windows Runtime (WRL)

Knihovna šablon C++ prostředí Windows Runtime (WRL) je knihovna šablon, která poskytuje způsob vytváření a používání prostředí Windows runtimech komponent na nízké úrovni.

> [!NOTE]
> WRL je teď nahrazený C++/WinRT, což je standardní projekce jazyka c++ 17 pro prostředí Windows Runtime API. C++/WinRT je k dispozici v sadě Windows 10 SDK od verze 1803 další. C++/WinRT je implementována zcela v hlavičkových souborech a je navržena tak, aby vám poskytovala prvotřídní přístup k modernímu rozhraní Windows API.
>
> Pomocí C++/WinRT můžete využívat i vytvářet prostředí Windows Runtime rozhraní API pomocí všech kompilátorů c++ 17 odpovídajících standardům. C++/WinRT obvykle provádí lepší a vytváří menší binární soubory než jakákoli jiná možnost jazyka pro prostředí Windows Runtime. Budeme dál podporovat C++/CX a WRL, ale důrazně doporučujeme, aby nové aplikace používaly C++/WinRT. Další informace najdete v tématu [ C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index).

## <a name="benefits"></a>Výhody

Knihovna šablon C++ prostředí Windows Runtime umožňuje snadněji implementovat a využívat komponenty modelu COM (Component Object Model). Poskytuje údržbu techniky, jako je počítání odkazů, pro správu životnosti objektů a testování hodnot HRESULT k určení, zda operace byla úspěšná nebo neúspěšná. Chcete-li úspěšně použít C++ knihovnu šablon prostředí Windows Runtime, je nutné pečlivě postupovat podle těchto pravidel a technik.

C++/CX je vysoce základní způsob použití prostředí Windows runtimech komponent na úrovni jazyka. Knihovna šablon prostředí Windows Runtime C++ i C++/CX zjednodušují psaní kódu pro prostředí Windows Runtime automatickým prováděním údržbu úloh vaším jménem.

Knihovna šablon C++ prostředí Windows Runtime a C++/CX poskytují různé výhody. Zde jsou některé důvody, proč možná budete chtít použít knihovnu C++ šablon prostředí Windows Runtime místo C++/CX:

- Knihovna C++ šablon prostředí Windows Runtime přidává do binárního rozhraní aplikace prostředí Windows Runtime (ABI) malou abstrakci, která vám dává možnost řídit podkladový kód pro lepší vytváření nebo zpracování rozhraní API prostředí Windows Runtime.

- C++/CX představuje hodnoty modelu COM HRESULT jako výjimky. Pokud jste zdědili základ kódu, který používá model COM, nebo který nepoužívá výjimky, můžete zjistit, že knihovna šablon C++ prostředí Windows Runtime je přirozenější způsob, jak pracovat s prostředí Windows Runtime, protože nemusíte používat výjimky.

   > [!NOTE]
   > Knihovna šablon C++ prostředí Windows Runtime používá hodnoty HRESULT a nevyvolává výjimky. Kromě toho knihovna šablon prostředí Windows Runtime C++ používá inteligentní ukazatele a vzor RAII k zajištění správného zničení objektů, když kód aplikace vyvolá výjimku. Další informace o inteligentních ukazatelích a RAII najdete v tématu věnovaném [inteligentním ukazatelům](../../cpp/smart-pointers-modern-cpp.md) a [objektům pro vlastní prostředky (RAII)](../../cpp/objects-own-resources-raii.md).

- Účel a návrh knihovny šablon prostředí Windows Runtime C++ nechte inspirovat knihovny ATL (Active Template Library), což je sada tříd založených na C++ šablonách, které zjednodušují programování objektů com. Vzhledem k C++ tomu, že knihovna C++ šablon prostředí Windows Runtime používá k zabalení prostředí Windows Runtime Standard, lze snadněji portovat a pracovat s mnoha EXISTUJÍCÍmi komponentami com napsanými v ATL do prostředí Windows Runtime. Pokud již znáte knihovnu ATL, můžete zjistit, že prostředí Windows Runtime C++ programování knihovny šablon je snazší.

## <a name="getting-started"></a>Začínáme

Tady je několik prostředků, které vám pomůžou pracovat s knihovnou C++ šablon prostředí Windows Runtime hned.

[Knihovna prostředí Windows Runtime (WRL)](https://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)<br/>
V tomto videu kanálu 9 se dozvíte víc o tom C++ , jak knihovna šablon prostředí Windows Runtime pomáhá psát aplikace Univerzální platforma Windows (UWP) a jak vytvářet a využívat prostředí Windows Runtime komponenty.

[Postupy: Aktivace a použití komponenty prostředí Windows Runtime](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)<br/>
Ukazuje, jak použít knihovnu šablon C++ prostředí Windows Runtime k inicializaci prostředí Windows Runtime a aktivaci a použití komponenty prostředí Windows Runtime.

[Postupy: Dokončit asynchronní operace](how-to-complete-asynchronous-operations-using-wrl.md)<br/>
Ukazuje, jak použít knihovnu šablon C++ prostředí Windows Runtime ke spuštění asynchronních operací a provedení práce po dokončení operací.

[Postupy: Zpracování událostí](how-to-handle-events-using-wrl.md)<br/>
Ukazuje, jak použít knihovnu šablon C++ prostředí Windows Runtime k přihlášení k odběru a zpracování událostí objektu prostředí Windows Runtime.

[Návod: Vytvoření aplikace pro UPW s použitím knihovny WRL a platformy Media Foundation](walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)<br/>
Naučte se, jak vytvořit aplikaci pro UWP, která používá [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk).

[Postupy: Vytvoření klasické komponenty modelu COM](how-to-create-a-classic-com-component-using-wrl.md)<br/>
Ukazuje, jak použít knihovnu šablon C++ prostředí Windows Runtime k vytvoření základní komponenty modelu COM a základní způsob, jak registrovat a spotřebovávat komponentu modelu COM z desktopové aplikace.

[Postupy: Přímé vytváření instancí komponent knihovny WRL](how-to-instantiate-wrl-components-directly.md)<br/>
Naučte se používat funkce [Microsoft:: WRL:: Make](make-function.md) a [Microsoft:: WRL::D Etails:: MakeAndInitialize](makeandinitialize-function.md) pro vytvoření instance komponenty z modulu, který ji definuje.

[Postupy: Vytváření souborů .h z metadat Windows pomocí nástrojů winmdidl.exe a midlrt.exe](use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)<br/>
Ukazuje, jak zpracovat vlastní součásti prostředí Windows Runtime z WRL vytvořením souboru IDL z metadat. winmd.

[Návod: Připojení pomocí úloh a žádostí XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Ukazuje, jak používat rozhraní [IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2) a [IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback) společně s úkoly k odesílání požadavků HTTP GET a post webové službě v aplikaci UWP.

[Ukázka optimalizace cest Bing Maps](https://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)<br/>
Používá třídu, která je definována v [návodu: `HttpRequest` Připojení pomocí úloh a požadavků](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) XML http v kontextu úplné aplikace UWP.

[Vytvoření komponenty prostředí Windows Runtime DLL s C++ ukázkou](https://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)<br/>
Ukazuje, jak pomocí knihovny šablon C++ prostředí Windows Runtime vytvořit vnitroprocesové komponentu knihovny DLL a spotřebovat ji z C++/CX, JavaScriptu a. C#

[Ukázka hry rozhraní DirectX mramor bludiště](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)<br/>
Ukazuje, jak použít knihovnu šablon C++ prostředí Windows Runtime ke správě životnosti komponent modelu COM, jako je rozhraní DirectX a Media Foundation v kontextu kompletní 3D hry.

[Ukázka odesílání oznámení informačních zpráv z desktopových aplikací](https://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)<br/>
Ukazuje, jak používat knihovnu šablon C++ prostředí Windows Runtime pro práci s informačními oznámeními z desktopové aplikace.

## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Knihovna C++ šablon prostředí Windows Runtime v porovnání s knihovnou ATL

Knihovna C++ šablon prostředí Windows Runtime připomíná knihovnu ATL (Active Template Library), protože ji můžete použít k vytvoření malých a rychlých objektů com. Prostředí Windows Runtime C++ knihovny šablon a ATL také sdílí koncepty, jako je definice objektů v modulech, explicitní registrace rozhraní a otevírání objektů pomocí továrn. Pokud jste obeznámeni s knihovnou ATL, můžete být spokojeni s prostředí Windows Runtime C++ knihovny šablon.

Knihovna C++ šablon prostředí Windows Runtime podporuje funkce modelu COM, které jsou požadovány pro aplikace pro UWP. Proto se liší od knihovny ATL, protože vynechává přímou podporu funkcí modelu COM, jako například:

- agregovat

- skladové implementace

- duální rozhraní (`IDispatch`)

- rozhraní Standard Enumerator

- body připojení

- odtrhnout rozhraní

- Vložení OLE

- ActiveX – ovládací prvky

- Model COM+

## <a name="concepts"></a>Koncepty

Knihovna C++ šablon prostředí Windows Runtime poskytuje typy, které představují několik základních konceptů. Tyto typy jsou popsány v následujících částech.

### <a name="comptr"></a>ComPtr

[ComPtr](comptr-class.md) je typ *inteligentního ukazatele* , který představuje rozhraní určené parametrem šablony. Použijte `ComPtr` k deklaraci proměnné, která má přístup k členům objektu, který je odvozen z rozhraní. `ComPtr`automaticky udržuje počet odkazů pro základní ukazatel rozhraní a uvolní rozhraní, když počet odkazů překročí nulu.

### <a name="runtimeclass"></a>RuntimeClass

[RuntimeClass](runtimeclass-class.md) představuje instanci třídy, která dědí sadu zadaných rozhraní. `RuntimeClass` Objekt může poskytnout kombinaci podpory pro jedno nebo více prostředí Windows Runtime rozhraní modelu COM nebo slabý odkaz na komponentu.

### <a name="module"></a>Modul

[Modul](module-class.md) představuje kolekci souvisejících objektů. `Module` Objekt spravuje objekty pro vytváření tříd, které vytvářejí objekty a registrují, což umožňuje jiným aplikacím použít objekt.

### <a name="callback"></a>OnCuePoint

Funkce [zpětného volání](callback-function-wrl.md) vytvoří objekt, jehož členská funkce je obslužná rutina události (metoda zpětného volání). `Callback` Použijte funkci k zápisu asynchronních operací.

### <a name="eventsource"></a>EventSource

[EventSource](eventsource-class.md) se používá ke správě obslužných rutin událostí *delegátů* . Použijte knihovnu C++ šablon prostředí Windows Runtime k implementaci delegáta a použijte `EventSource` k přidání, odebrání a vyvolání delegátů.

### <a name="asyncbase"></a>AsyncBase

[AsyncBase](asyncbase-class.md) poskytuje virtuální metody, které představují prostředí Windows Runtime asynchronní programovací model. Přepište členy v této třídě a vytvořte tak vlastní třídu, která může spustit, zastavit nebo kontrolovat průběh asynchronní operace.

### <a name="ftmbase"></a>FtmBase

[FtmBase](ftmbase-class.md) představuje objekt zařazovací modul s volnými vlákny. `FtmBase`vytvoří globální tabulku rozhraní (GIT) a pomůže spravovat zařazovací a proxy objekty.

### <a name="weakref"></a>WeakRef

[WeakRef](weakref-class.md) je typ inteligentního ukazatele, který představuje *slabý odkaz*, který odkazuje na objekt, který může nebo nemusí být přístupný. `WeakRef` Objekt může být použit pouze pomocí prostředí Windows Runtime, a ne podle klasického modelu COM.

`WeakRef` Objekt obvykle představuje objekt, jehož existence je řízena externím vláknem nebo aplikací. `WeakRef` Objekt může například odkazovat na objekt souboru. Když je soubor otevřený, `WeakRef` je platný a odkazovaný soubor je přístupný. Ale když je soubor zavřený, `WeakRef` je neplatný a soubor není přístupný.

## <a name="related-topics"></a>Související témata

|||
|-|-|
|[Klíčová rozhraní API podle kategorie](key-wrl-apis-by-category.md)|Zvýrazní typy, funkce C++ a makra primární knihovny šablon prostředí Windows Runtime.|
|[Referenční informace](wrl-reference.md)|Obsahuje referenční informace pro knihovnu šablon C++ prostředí Windows Runtime.|
|[Rychlý referenční C++pro/CX)](../../cppcx/quick-reference-c-cx.md)|Stručně popisuje C++funkce/CX, které podporují prostředí Windows Runtime.|
|[Používání komponent prostředí Windows Runtime v jazyce VisualC++](/windows/uwp/winrt-components/walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp)|Ukazuje, jak použít C++/CX k vytvoření základní komponenty prostředí Windows Runtime.|
