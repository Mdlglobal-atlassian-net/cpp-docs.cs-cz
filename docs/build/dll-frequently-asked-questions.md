---
title: Knihovny MFC DLL – nejčastější dotazy
ms.date: 11/04/2016
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 33a0c9dd1abbfb9375ce1aef53fd152a521ac97d
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "57821934"
---
# <a name="dll-frequently-asked-questions"></a>DLL – nejčastější dotazy

Toto jsou některé nejčastější dotazy (FAQ) o knihovnách DLL.

- [Knihovna MFC DLL vytvořit více vláken?](#mfc_multithreaded_1)

- [Může Vícevláknová aplikace přistupovat ke knihovně MFC DLL v různých vláknech?](#mfc_multithreaded_2)

- [Existují jakékoli třídy nebo funkce MFC, které nelze použít v knihovně MFC DLL?](#mfc_prohibited_classes)

- [Jaké optimalizační techniky mám použít ke zlepšení výkonu klientské aplikace při načítání?](#mfc_optimization)

- [Běžná knihovna DLL MFC je nevracení paměti, ale vypadá dobře můj kód. Jak zjistím nevracení paměti?](#memory_leak)

## <a name="mfc_multithreaded_1"></a> Knihovna MFC DLL vytvořit více vláken?

S výjimkou během inicializace knihovny MFC DLL můžete bezpečně vytvořit více vláken tak dlouho, dokud používá místní úložiště (TLS) funkce, jako například Win32 vlákno **TlsAlloc** přidělit úložiště thread local. Nicméně pokud používá knihovny MFC DLL **__declspec(thread)** přidělit úložiště thread local, klientská aplikace musí implicitně propojit do knihovny DLL. Pokud klientská aplikace explicitně odkazovat na knihovnu DLL, volání **LoadLibrary** nebude úspěšně načíst knihovnu DLL. Další informace o proměnných místního vlákna v knihovnách DLL naleznete v tématu [vlákno](../cpp/thread.md).

Knihovna MFC DLL, která při spuštění vytvoří nové vlákno MFC přestane reagovat při načtení aplikace. Jedná se o pokaždé, když vlákno je vytvořen zavoláním `AfxBeginThread` nebo `CWinThread::CreateThread` uvnitř:

- `InitInstance` z `CWinApp`-odvozenému objektu v běžné knihovny MFC DLL.

- Zadaného `DllMain` nebo **RawDllMain** funkce v běžné knihovny MFC DLL.

- Zadaného `DllMain` nebo **RawDllMain** funkce v rozšiřující knihovny DLL MFC.

## <a name="mfc_multithreaded_2"></a> Může Vícevláknová aplikace přistupovat ke knihovně MFC DLL v různých vláknech?

Vícevláknové aplikace můžou k běžných knihovnách MFC DLL, která dynamicky propojené ke knihovně MFC a rozšiřující knihovny DLL MFC z různých vláken. A od verze Visual C++ verze 4.2, mají přístup aplikace k běžných knihovnách MFC DLL, která staticky se propojit s knihovnou MFC z více vláken v aplikaci.

Starší než verze 4.2 pouze jedno vlákno externí přiložit běžné knihovny MFC DLL staticky propojené do MFC.

Všimněte si, že v dokumentaci k Visual C++ se již nepoužívá termín USRDLL. Běžné knihovny MFC DLL staticky propojené do MFC má stejné vlastnosti jako dosavadní USRDLL.

## <a name="mfc_prohibited_classes"></a> Existují jakékoli třídy nebo funkce MFC, které nelze použít v knihovně MFC DLL?

Použití knihoven DLL rozšíření `CWinApp`-odvozené třídy klientské aplikace. Nesmí mít svou vlastní `CWinApp`-odvozené třídy.

regulární knihovny DLL MFC musí mít `CWinApp`-odvozené třídy a jeden objekt třídy aplikace, stejně jako aplikace knihovny MFC. Na rozdíl od `CWinApp` objektu aplikace `CWinApp` objekt knihovny DLL nemá hlavní zprávy odeslané.

Upozorňujeme, že `CWinApp::Run` mechanismus se nevztahují na knihovnu DLL, aplikace vlastní hlavní pumpu zpráv. Pokud knihovna DLL otevře nemodálních dialogových oken nebo má vlastní okna hlavního rámce, pumpa zpráv aplikace musí volat rutinu exportovaných knihovnou DLL, která pak volá `CWinApp::PreTranslateMessage` členské funkce objektu aplikaci knihovny DLL.

## <a name="mfc_optimization"></a> Jaké optimalizační techniky mám použít ke zlepšení klientská aplikace&#39;s výkon při načítání?

Pokud vaše knihovna DLL je běžné knihovny MFC DLL, která je staticky propojena s knihovnou MFC, změnu na běžný knihovny MFC DLL, která je dynamicky propojena s knihovnou MFC snižuje velikost souboru.

Pokud má knihovna DLL mnoho exportovaných funkcí, použijte soubor .def export funkcí (namísto použití **__declspec(dllexport)**) a použijte soubor .def [NONAME – atribut](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) na každém exportované funkce. NONAME – atribut způsobí, že pouze pořadové číslo a ne název funkce mají být uloženy v exportní tabulce knihovny DLL, což snižuje velikost souboru.

Knihovny DLL, které jsou implicitně propojené do aplikace jsou načteny při načtení aplikace. Pro zlepšení výkonu při načítání, zkuste rozdělit do různých knihoven DLL knihovnu DLL. Všechny funkce, které potřebuje volající aplikace ihned po načtení do jedné knihovny DLL a je volající aplikace implicitně odkaz na tuto knihovnu DLL. Další funkce, které volající aplikace nemusí okamžitě do jiné knihovně DLL a mají aplikace explicitně odkaz na tuto knihovnu DLL. Další informace najdete v tématu [propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).

## <a name="memory_leak"></a> Existuje&#39;vypadá dobře s nevracení paměti v Běžná knihovna DLL MFC, ale můj kód. Jak zjistím nevracení paměti?

Jednou z možných příčin nevracení paměti je, že knihovna MFC vytvoří dočasné objekty, které se používají v rámci funkcí obslužných rutin zpráv. V aplikacích MFC tyto dočasné objekty se automaticky vyčistí v `CWinApp::OnIdle()` funkce, která je volána mezi zpracování zpráv. Nicméně v MFC dynamické knihovny (DLL) `OnIdle()` funkce není volána automaticky. V důsledku toho dočasné objekty nejsou vyčištění automaticky. Vyčistit dočasné objekty, musí explicitně volat knihovny DLL `OnIdle(1)` pravidelně.

## <a name="see-also"></a>Viz také:

[Knihovny DLL v jazyce Visual C++](dlls-in-visual-cpp.md)
