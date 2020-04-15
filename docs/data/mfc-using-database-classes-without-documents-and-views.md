---
title: 'MFC: Použití databázových tříd bez objektů Document a View'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC applications [C++], without views
- documents [C++], applications without
- ODBC applications [C++]
- document/view architecture [C++], in databases
- files [C++], MFC
- database classes [C++], MFC
- CRecordView class, using in database applications
- database applications [C++], without views
- database applications [C++], application wizard options
- application wizards [C++], creating database applications
- ODBC [C++], file support in database applications
- ODBC applications [C++], without documents
- database applications [C++], without documents
- user interface [C++], drawing information
ms.assetid: 15bf52d4-91cf-4b1d-8b37-87c3ae70123a
ms.openlocfilehash: c914a449b73e7da876d2e05b894c016b53881c3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360674"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC: Použití databázových tříd bez objektů Document a View

Někdy možná nebudete chtít použít architekturu dokumentu a zobrazení rozhraní v databázových aplikacích. Toto téma vysvětluje:

- [Pokud nepotřebujete použít dokumenty,](#_core_when_you_don.92.t_need_documents) jako je serializace dokumentu.

- [Možnosti Průvodce aplikací](#_core_appwizard_options_for_documents_and_views) podporují aplikace bez serializace a bez příkazů nabídky **Soubor** souvisejících s dokumentem, například **New**, **Open**, **Save**a **Save As**.

- [Jak pracovat s aplikací, která používá minimální dokument](#_core_applications_with_minimal_documents).

- [Jak strukturovat aplikaci bez dokumentu nebo zobrazení](#_core_applications_with_no_document).

## <a name="when-you-do-not-need-documents"></a><a name="_core_when_you_don.92.t_need_documents"></a>Když nepotřebujete dokumenty

Některé aplikace mají odlišný koncept dokumentu. Tyto aplikace obvykle načítají všechny nebo většinu souboru z úložiště do paměti pomocí příkazu **Otevřít soubor.** Zapisují aktualizovaný soubor zpět do úložiště najednou pomocí příkazu **Uložit soubor** nebo **Uložit jako.** Co uživatel vidí, je datový soubor.

Některé kategorie aplikací však dokument nevyžadují. Databázové aplikace fungují z hlediska transakcí. Aplikace vybírá záznamy z databáze a prezentuje je uživateli, často jeden po druhém. Uživatel vidí obvykle jeden aktuální záznam, který může být jediný v paměti.

Pokud vaše aplikace nevyžaduje dokument pro ukládání dat, můžete upustit od některé nebo všechny architektury dokumentu nebo zobrazení rozhraní. Jak moc se obejít, závisí na přístupu, který dáváte přednost. Můžete:

- Použijte minimální dokument jako místo pro uložení připojení ke zdroji dat, ale upustit od normálních funkcí dokumentu, jako je serializace. To je užitečné, pokud chcete několik zobrazení dat a chcete synchronizovat všechna zobrazení, aktualizovat je všechny najednou a tak dále.

- Použijte okno rámce, do kterého kreslíte přímo, místo zobrazení. V takovém případě vynechete dokument a uložíte všechna data nebo datová připojení do objektu okna rámce.

## <a name="application-wizard-options-for-documents-and-views"></a><a name="_core_appwizard_options_for_documents_and_views"></a>Možnosti Průvodce aplikací pro dokumenty a zobrazení

Průvodce aplikací knihovny MFC má několik možností v **podpoře databáze Select**, které jsou uvedeny v následující tabulce. Pokud k vytvoření aplikace použijete Průvodce aplikací knihovny MFC, všechny tyto možnosti vytvoří aplikace s dokumenty a zobrazeními. Některé možnosti poskytují dokumenty a zobrazení, které vynechují nepotřebné funkce dokumentu. Další informace naleznete v [tématu Podpora databáze, Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md).

|Možnost|Zobrazit|Dokument|
|------------|----------|--------------|
|**Žádné**|Odvozeno `CView`od .|Poskytuje žádnou podporu databáze. Toto je výchozí možnost.<br /><br /> Pokud vyberete možnost **Podpora architektury Dokument/zobrazení** na stránce [Typ aplikace, Průvodce aplikací knihovny MFC,](../mfc/reference/application-type-mfc-application-wizard.md) získáte plnou podporu dokumentu včetně serializace a příkazů **New**, **Open**, **Save**a **Save As** v nabídce **Soubor.** Viz [Aplikace bez dokumentu](#_core_applications_with_no_document).|
|**Pouze soubory záhlaví**|Odvozeno `CView`od .|Poskytuje základní úroveň podpory databáze pro vaši aplikaci.<br /><br /> Zahrnuje Afxdb.h. Přidá knihovny odkazů, ale nevytvoří žádné třídy specifické pro databázi. Sady záznamů můžete vytvořit později a použít je ke kontrole a aktualizaci záznamů.|
|**Zobrazení databáze bez podpory souborů**|Odvozeno od`CRecordView`|Poskytuje podporu dokumentů, ale žádnou podporu serializace. Dokument může ukládat sadu záznamů a koordinovat více zobrazení; nepodporuje serializaci nebo příkazy **New**, **Open**, **Save**a **Save As.** Viz [Aplikace s minimálními dokumenty](#_core_applications_with_minimal_documents). Pokud zahrnete zobrazení databáze, je nutné zadat zdroj dat.<br /><br /> Zahrnuje soubory hlaviček databáze, knihovny odkazů, zobrazení záznamů a sadu záznamů. (K dispozici pouze pro aplikace s možností **podpory architektury dokument/zobrazení** vybrané na stránce [Typ aplikace, Průvodce aplikací knihovny MFC.)](../mfc/reference/application-type-mfc-application-wizard.md)|
|**Zobrazení databáze s podporou souborů**|Odvozeno od`CRecordView`|Poskytuje úplnou podporu dokumentu, včetně serializace a příkazů nabídky **souborsouvisejících** s dokumentem. Databázové aplikace obvykle pracují na základě pro každý záznam, nikoli na základě pro každý soubor, a proto nepotřebují serializaci. Však může mít zvláštní použití pro serializaci. Viz [Aplikace s minimálními dokumenty](#_core_applications_with_minimal_documents). Pokud zahrnete zobrazení databáze, je nutné zadat zdroj dat.<br /><br /> Zahrnuje soubory hlaviček databáze, knihovny odkazů, zobrazení záznamů a sadu záznamů. (K dispozici pouze pro aplikace s možností **podpory architektury dokument/zobrazení** vybrané na stránce [Typ aplikace, Průvodce aplikací knihovny MFC.)](../mfc/reference/application-type-mfc-application-wizard.md)|

Diskuse o alternativách serializace a alternativní použití pro serializaci, naleznete v [tématu Serializace: Serializace vs. vstup databáze/výstup](../mfc/serialization-serialization-vs-database-input-output.md).

## <a name="applications-with-minimal-documents"></a><a name="_core_applications_with_minimal_documents"></a>Aplikace s minimálními dokumenty

Průvodce aplikací knihovny MFC má dvě možnosti, které podporují aplikace pro přístup k datům založené na formuláři. Každá možnost `CRecordView`vytvoří odvozenou třídu zobrazení a dokument. Liší se v tom, co z dokumentu vynechávají.

### <a name="document-without-file-support"></a><a name="_core_a_document_without_file_support"></a>Dokument bez podpory souborů

Pokud nepotřebujete serializaci dokumentu, vyberte možnost Databáze průvodce aplikací **bez podpory souborů.** Dokument slouží k následujícím užitečným účelům:

- Je to vhodné místo `CRecordset` pro uložení objektu.

   Toto použití paralely běžné koncepty dokumentu: dokument ukládá data (nebo v tomto případě sadu záznamů) a zobrazení je zobrazení dokumentu.

- Pokud aplikace obsahuje více zobrazení (například více zobrazení záznamů), dokument podporuje koordinaci zobrazení.

   Pokud více zobrazení zobrazují stejná data, můžete pomocí `CDocument::UpdateAllViews` členské funkce koordinovat aktualizace všech zobrazení při změně dat v libovolném zobrazení.

Tuto možnost obvykle používáte pro jednoduché aplikace založené na formuláři. Průvodce aplikací podporuje pohodlnou strukturu pro tyto aplikace automaticky.

### <a name="document-with-file-support"></a><a name="_core_a_document_with_file_support"></a>Dokument s podporou souborů

Vyberte možnost Databáze průvodce aplikací Zobrazení databáze **s podporou souborů,** pokud máte alternativní použití pro příkazy nabídky **souboru** související s dokumentem a serializaci dokumentu. Pro část programu pro přístup k datům můžete dokument použít stejným způsobem, jak je popsáno v [dokumentu bez podpory souborů](#_core_a_document_without_file_support). Možnost serializace dokumentu můžete použít například ke čtení a zápisu serializovaného dokumentu profilu uživatele, který ukládá předvolby uživatele nebo jiné užitečné informace. Další nápady naleznete v [tématu Serializace: Serializace vs. Vstup/výstup databáze](../mfc/serialization-serialization-vs-database-input-output.md).

Průvodce aplikací tuto možnost podporuje, ale je nutné napsat kód, který serializuje dokument. Serializované informace uložte do datových členů dokumentu.

## <a name="applications-with-no-document"></a><a name="_core_applications_with_no_document"></a>Aplikace bez dokumentu

Někdy můžete chtít napsat aplikaci, která nepoužívá dokumenty nebo zobrazení. Bez dokumentů uložte data (například `CRecordset` objekt) ve třídě okna rámce nebo ve třídě aplikace. Další požadavky závisí na tom, zda aplikace představuje uživatelské rozhraní.

### <a name="database-support-with-a-user-interface"></a><a name="_core_database_support_with_a_user_interface"></a>Podpora databáze s uživatelským rozhraním

Pokud máte uživatelské rozhraní (jiné než například rozhraní příkazového řádku konzoly), aplikace nakreslí přímo do klientské oblasti okna rámce, nikoli do zobrazení. Taková aplikace nepoužívá `CRecordView`, `CFormView`, `CDialog` , nebo pro své hlavní `CDialog` uživatelské rozhraní, ale obvykle se používá pro běžné dialogy.

### <a name="writing-applications-without-documents"></a><a name="_core_writing_applications_without_documents"></a>Psaní žádostí bez dokumentů

Vzhledem k tomu, že průvodce aplikací nepodporuje `CWinApp`vytváření aplikací bez dokumentů, musíte napsat `CFrameWnd` `CMDIFrameWnd` vlastní odvozenou třídu a v případě potřeby také vytvořit třídu nebo. Přepsat `CWinApp::InitInstance` a deklarovat objekt aplikace jako:

```cpp
CYourNameApp theApp;
```

Rámec stále poskytuje mechanismus mapy zpráv a mnoho dalších funkcí.

### <a name="database-support-separate-from-the-user-interface"></a><a name="_core_database_support_separate_from_the_user_interface"></a>Podpora databáze oddělená od uživatelského rozhraní

Některé aplikace nepotřebují žádné uživatelské rozhraní nebo pouze minimální. Předpokládejme například, že píšete:

- Zprostředkující objekt přístupu k datům, který jiné aplikace (klienti) vyžadují zvláštní zpracování dat mezi aplikací a zdrojem dat.

- Aplikace, která zpracovává data bez zásahu uživatele, například aplikace, která přesouvá data z jednoho formátu databáze do jiného nebo aplikace, která provádí výpočty a provádí dávkové aktualizace.

Protože žádný dokument `CRecordset` vlastní objekt, pravděpodobně jej chcete uložit jako vložený datový člen ve vaší `CWinApp`odvozené třídě aplikace. Alternativy zahrnují:

- Neudržet trvalý `CRecordset` předmět vůbec. Konstruktorům třídy sady záznamů můžete předat hodnotu NULL. V takovém případě rozhraní vytvoří `CDatabase` dočasný objekt pomocí informací v `GetDefaultConnect` členské funkci sady záznamů. To je nejpravděpodobnější alternativní přístup.

- Vytvoření `CRecordset` objektu globální proměnné. Tato proměnná by měla být ukazatelem na objekt `CWinApp::InitInstance` sady záznamů, který vytvoříte dynamicky v přepsání. Tím se zabrání pokusu o vytvoření objektu před inicializována rámci.

- Použití objektů sady záznamů stejně jako v kontextu dokumentu nebo zobrazení. Vytvořte sady záznamů v členských funkcích objektů aplikace nebo frame-window.

## <a name="see-also"></a>Viz také

[Třídy databáze knihovny MFC](../data/mfc-database-classes-odbc-and-dao.md)
