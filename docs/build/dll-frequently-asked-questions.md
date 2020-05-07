---
title: Nejčastější dotazy ke knihovnám MFC DLL
ms.date: 05/06/2019
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 9108aaf3fcface847b0391455a2aecd4d45658c4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417346"
---
# <a name="dll-frequently-asked-questions"></a>DLL – nejčastější dotazy

Následují Nejčastější dotazy týkající se knihoven DLL.

- [Může knihovna MFC DLL vytvořit více vláken?](#mfc_multithreaded_1)

- [Může vícevláknová aplikace přistupovat k knihovně MFC DLL v různých vláknech?](#mfc_multithreaded_2)

- [Existují nějaké třídy nebo funkce knihovny MFC, které nelze použít v knihovně MFC DLL?](#mfc_prohibited_classes)

- [Jaké optimalizační techniky mám použít ke zlepšení výkonu klientské aplikace při načítání?](#mfc_optimization)

- [V běžné knihovně MFC DLL je nevrácená paměť, ale můj kód vypadá dobře. Jak můžu najít nevrácenou paměť?](#memory_leak)

## <a name="can-an-mfc-dll-create-multiple-threads"></a><a name="mfc_multithreaded_1"></a>Může knihovna MFC DLL vytvořit více vláken?

S výjimkou během inicializace může knihovna MFC DLL bezpečně vytvořit více vláken, pokud používá funkce úložiště Win32 thread local (TLS), jako je například **TlsAlloc** , k přidělení Thread Local úložiště. Pokud však knihovna MFC DLL používá **__declspec (thread)** k přidělení Thread Local úložiště, musí být klientská aplikace implicitně propojena s knihovnou DLL. Pokud klientská aplikace explicitně odkazuje na knihovnu DLL, volání funkce **LoadLibrary** nebude knihovnu DLL úspěšně načtena. Další informace o proměnných místních vláken v knihovnách DLL naleznete v tématu [thread](../cpp/thread.md).

Knihovna MFC DLL, která vytvoří nové vlákno MFC během spuštění, přestane reagovat, když je načten aplikací. To zahrnuje pokaždé, když je vlákno vytvořeno `AfxBeginThread` voláním nebo `CWinThread::CreateThread` uvnitř:

- Objekt `InitInstance` odvozený `CWinApp`od objektu v běžné knihovně MFC DLL.

- Dodaná `DllMain` nebo **RawDllMain** funkce v běžné knihovně MFC DLL.

- Dodaná `DllMain` nebo **RawDllMain** funkce v rozšiřující knihovně MFC knihovny MFC.

## <a name="can-a-multithreaded-application-access-an-mfc-dll-in-different-threads"></a><a name="mfc_multithreaded_2"></a>Může vícevláknová aplikace přistupovat k knihovně MFC DLL v různých vláknech?

Aplikace s více vlákny mají přístup k běžným knihovnám MFC DLL, které dynamicky propojí s knihovnami DLL rozšíření MFC a MFC z různých vláken. Aplikace má přístup k běžným knihovnám MFC DLL, které staticky odkazují na knihovnu MFC z více vláken vytvořených v aplikaci.

## <a name="are-there-any-mfc-classes-or-functions-that-cannot-be-used-in-an-mfc-dll"></a><a name="mfc_prohibited_classes"></a>Existují nějaké třídy nebo funkce knihovny MFC, které nelze použít v knihovně MFC DLL?

Rozšiřující knihovny DLL používají `CWinApp`třídu odvozenou z klientské aplikace. Nesmí mít svou vlastní `CWinApp`odvozenou třídu.

Běžné knihovny MFC DLL musí mít `CWinApp`třídu odvozenou od třídy a jeden objekt třídy aplikace, stejně jako aplikace MFC. Na rozdíl od `CWinApp` objektu aplikace nemá `CWinApp` objekt knihovny DLL hlavní čerpadlo zpráv.

Všimněte si, že `CWinApp::Run` vzhledem k tomu, že mechanismus neplatí pro knihovnu DLL, aplikace vlastní hlavní pumpu zpráv. Pokud knihovna DLL otevře nemodální dialogová okna nebo má hlavní okno rámce vlastní, musí hlavní pumpa zpráv aplikace volat rutinu exportovanou, která je exportována knihovnou DLL, která `CWinApp::PreTranslateMessage` zase volá členskou funkci objektu aplikace knihovny DLL.

## <a name="what-optimization-techniques-should-i-use-to-improve-the-client-application39s-performance-when-loading"></a><a name="mfc_optimization"></a>Jaké techniky optimalizace mám použít ke zlepšení výkonu&#39;klientských aplikací při načítání?

Pokud je vaše knihovna DLL běžná knihovna MFC DLL, která je staticky propojena s KNIHOVNou MFC, její změna na regulární knihovnu MFC DLL, která je dynamicky propojena s knihovnou MFC, zmenšuje velikost souboru.

Pokud má knihovna DLL velký počet exportovaných funkcí, použijte soubor. def k exportu funkcí (namísto použití **__declspec (dllexport)**) a pro každou exportovanou funkci použijte [Atribut NONAME](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) souboru. def. Atribut NONAME způsobí, že pouze pořadové hodnoty a nikoli název funkce budou uloženy v exportní tabulce knihovny DLL, což zmenšuje velikost souboru.

Knihovny DLL, které jsou implicitně propojeny s aplikací, jsou načteny při načtení aplikace. Chcete-li zlepšit výkon při načítání, zkuste rozdělit knihovnu DLL do různých knihoven DLL. Všechny funkce, které volající aplikace potřebuje hned po načtení do jedné knihovny DLL a které mají volající aplikaci implicitně propojit s touto knihovnou DLL. Vložte další funkce, které volající aplikace nepotřebuje hned, do jiné knihovny DLL a aplikace musí explicitně propojit s touto knihovnou DLL. Další informace najdete v tématu [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).

## <a name="there39s-a-memory-leak-in-my-regular-mfc-dll-but-my-code-looks-fine-how-can-i-find-the-memory-leak"></a><a name="memory_leak"></a>V běžné knihovně MFC DLL&#39;nevracení paměti, ale můj kód vypadá dobře. Jak můžu najít nevrácenou paměť?

Jednou z možných příčin nevracení paměti je, že knihovna MFC vytvoří dočasné objekty, které jsou používány v rámci funkcí obslužných rutin zpráv. V aplikacích MFC jsou tyto dočasné objekty automaticky vyčištěny ve `CWinApp::OnIdle()` funkci, která je volána mezi zpracováním zpráv. V knihovnách DLL (Dynamic-Link Library) knihovny MFC však `OnIdle()` funkce není volána automaticky. V důsledku toho nebudou dočasné objekty automaticky vyčištěny. Chcete-li vyčistit dočasné objekty, knihovna DLL musí explicitně `OnIdle(1)` volat pravidelně.

## <a name="see-also"></a>Viz také

[Vytváření knihoven DLL jazyka C/C++ v aplikaci Visual Studio](dlls-in-visual-cpp.md)
