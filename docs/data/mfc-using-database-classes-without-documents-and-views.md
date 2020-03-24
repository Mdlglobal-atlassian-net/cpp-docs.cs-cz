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
ms.openlocfilehash: 57a7abd89bc9bfb465912a35c21f9780668f4466
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213353"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC: Použití databázových tříd bez objektů Document a View

Někdy možná nebudete chtít v databázových aplikacích použít architekturu dokument/zobrazení rozhraní. Toto téma vysvětluje:

- [Pokud nepotřebujete používat dokumenty](#_core_when_you_don.92.t_need_documents) , jako je například serializace dokumentu.

- [Možnosti Průvodce aplikací](#_core_appwizard_options_for_documents_and_views) pro podporu aplikací bez serializace a bez příkazů nabídky **souborů** souvisejících s dokumentem, jako je například **Nový**, **otevřít**, **Uložit**a **Uložit jako**.

- [Jak pracovat s aplikací, která používá minimální dokument](#_core_applications_with_minimal_documents).

- [Postup strukturování aplikace bez dokumentu nebo zobrazení](#_core_applications_with_no_document)

##  <a name="when-you-do-not-need-documents"></a><a name="_core_when_you_don.92.t_need_documents"></a>Pokud nepotřebujete dokumenty

Některé aplikace mají jedinečný koncept dokumentu. Tyto aplikace obvykle načtou do paměti všechny soubory nebo většinu souborů z úložiště pomocí příkazu pro **otevření souboru** . Napíší aktualizovaný soubor zpátky do úložiště pomocí příkazu **soubor uložit** nebo **Uložit jako** . To, co uživatel vidí, je datový soubor.

Některé kategorie aplikací ale nevyžadují dokument. Databázové aplikace fungují v souvislosti s transakcemi. Aplikace vybere záznamy z databáze a prezentuje je uživateli, často v jednom okamžiku. To, co uživatel vidí, je obvykle jediný aktuální záznam, který může být jediným z nich v paměti.

Pokud vaše aplikace nevyžaduje dokument pro ukládání dat, můžete s architekturou dokumentu/zobrazení architektury obejít. Záleží na tom, kolik máte přístup k vašemu přístupu. Možná:

- Použijte minimální dokument jako místo pro uložení připojení ke zdroji dat, ale s využitím normálních funkcí dokumentů, jako je například serializace. To je užitečné, když chcete několik zobrazení dat a chcete synchronizovat všechna zobrazení, aktualizovat je všechny najednou a tak dále.

- Použijte okno rámce, do kterého přímo nakreslíte místo použití zobrazení. V tomto případě vynecháte dokument a uložíte všechna data nebo datová připojení v objektu Frame-Window.

##  <a name="application-wizard-options-for-documents-and-views"></a><a name="_core_appwizard_options_for_documents_and_views"></a>Možnosti Průvodce aplikací pro dokumenty a zobrazení

Průvodce aplikací knihovny MFC má několik možností v rámci **podpory výběru databáze**, které jsou uvedeny v následující tabulce. Použijete-li Průvodce aplikací knihovny MFC k vytvoření aplikace, všechny tyto možnosti vytvoří aplikace s dokumenty a zobrazeními. Některé možnosti poskytují dokumenty a zobrazení, které vynechávají nepotřebnou funkci dokumentu. Další informace naleznete v tématu [Podpora databáze, Průvodce aplikací MFC](../mfc/reference/database-support-mfc-application-wizard.md).

|Možnost|Zobrazit|Dokument|
|------------|----------|--------------|
|**NTato**|Odvozeno z `CView`.|Neposkytuje žádnou podporu databáze. Toto je výchozí možnost.<br /><br /> Vyberete-li možnost **Podpora architektury dokument/zobrazení** na stránce [Typ aplikace, Průvodce aplikací knihovny MFC](../mfc/reference/application-type-mfc-application-wizard.md) , získáte úplnou podporu dokumentu včetně serializace a **nových**, **otevřených**, **ukládání**a **ukládání jako** příkazů v nabídce **soubor** . Viz [aplikace bez dokumentu](#_core_applications_with_no_document).|
|**Pouze hlavičkové soubory**|Odvozeno z `CView`.|Poskytuje základní úroveň podpory databáze pro vaši aplikaci.<br /><br /> Zahrnuje AFXDB. h. Přidá knihovny odkazů, ale nevytváří žádné třídy specifické pro databázi. Můžete vytvořit sady záznamů později a použít je ke kontrole a aktualizaci záznamů.|
|**Zobrazení databáze bez podpory souborů**|Odvozeno od `CRecordView`|Poskytuje podporu dokumentu, ale nepodporuje serializaci. Dokument může ukládat sady záznamů a koordinovat více zobrazení; nepodporuje serializace ani příkazy **New**, **Open**, **Save**a **Save jako** . Zobrazit [aplikace s minimálními dokumenty](#_core_applications_with_minimal_documents) Pokud zahrnete zobrazení databáze, musíte zadat zdroj dat.<br /><br /> Zahrnuje hlavičkové soubory databáze, propojení knihoven, zobrazení záznamů a sadu záznamů. (K dispozici pouze pro aplikace s možností **Podpora architektury dokument/zobrazení** , která je vybrána na stránce [Typ aplikace, Průvodce aplikací knihovny MFC](../mfc/reference/application-type-mfc-application-wizard.md) .)|
|**Zobrazení databáze s podporou souborů**|Odvozeno od `CRecordView`|Poskytuje úplnou podporu dokumentu, včetně serializace a příkazů nabídky **souborů** souvisejících s dokumentem. Databázové aplikace obvykle pracují na jednotlivých záznamech, nikoli na základě jednotlivých souborů a nepotřebují serializaci. Je však možné, že máte speciální použití pro serializaci. Zobrazit [aplikace s minimálními dokumenty](#_core_applications_with_minimal_documents) Pokud zahrnete zobrazení databáze, musíte zadat zdroj dat.<br /><br /> Zahrnuje hlavičkové soubory databáze, propojení knihoven, zobrazení záznamů a sadu záznamů. (K dispozici pouze pro aplikace s možností **Podpora architektury dokument/zobrazení** , která je vybrána na stránce [Typ aplikace, Průvodce aplikací knihovny MFC](../mfc/reference/application-type-mfc-application-wizard.md) .)|

Diskuzi o alternativách k serializaci a alternativním použití pro serializaci naleznete v tématu [serializace: serializace vs. vstup/výstup databáze](../mfc/serialization-serialization-vs-database-input-output.md).

##  <a name="applications-with-minimal-documents"></a><a name="_core_applications_with_minimal_documents"></a>Aplikace s minimálními dokumenty

Průvodce aplikací knihovny MFC má dvě možnosti, které podporují aplikace pro přístup k datům založené na formulářích. Každá možnost vytvoří třídu zobrazení odvozené `CRecordView`a dokument. Liší se v tom, co z dokumentu odejdou.

###  <a name="document-without-file-support"></a><a name="_core_a_document_without_file_support"></a>Dokument bez podpory souborů

Pokud nepotřebujete serializaci dokumentu, vyberte možnost databáze Průvodce aplikací v **zobrazení databáze bez podpory souborů** . Dokument slouží jako užitečné pro následující účely:

- Je to vhodné místo pro uložení objektu `CRecordset`.

   Toto využití paralelně využívá běžné koncepty dokumentů: dokument ukládá data (nebo v tomto případě sadu záznamů) a zobrazení je zobrazení dokumentu.

- Pokud vaše aplikace prezentuje více zobrazení (například více zobrazení záznamů), dokument podporuje koordinaci zobrazení.

   Pokud více zobrazení zobrazuje stejná data, můžete použít členskou funkci `CDocument::UpdateAllViews` k koordinaci aktualizací všech zobrazení, když jakékoli zobrazení změní data.

Tuto možnost obvykle používáte pro jednoduché aplikace založené na formulářích. Průvodce aplikací podporuje pro tyto aplikace pohodlný strukturu automaticky.

###  <a name="document-with-file-support"></a><a name="_core_a_document_with_file_support"></a>Dokument s podporou souborů

Pokud máte alternativní použití pro příkazy nabídky **soubor** souvisejících s dokumentem a serializaci dokumentu, vyberte možnost databáze Průvodce aplikace **s podporou souborů** . Pro datovou část programu můžete dokument použít stejným způsobem, jaký je popsaný v [dokumentu bez podpory souborů](#_core_a_document_without_file_support). Můžete použít funkci serializace dokumentu, například ke čtení a zápisu serializovaného dokumentu profilu uživatele, který ukládá předvolby uživatele nebo jiné užitečné informace. Další nápady najdete v tématu [serializace: serializace vs. vstup/výstup databáze](../mfc/serialization-serialization-vs-database-input-output.md).

Průvodce aplikací podporuje tuto možnost, ale je nutné napsat kód, který dokument serializovat. Uložit serializované informace do datových členů dokumentu.

##  <a name="applications-with-no-document"></a><a name="_core_applications_with_no_document"></a>Aplikace bez dokumentu

Někdy můžete chtít napsat aplikaci, která nepoužívá dokumenty ani zobrazení. Bez dokumentů ukládáte vaše data (například `CRecordset` objekt) do vaší třídy oken s rámečkem nebo vaší třídy aplikace. Jakékoli další požadavky závisí na tom, zda aplikace prezentuje uživatelské rozhraní.

###  <a name="database-support-with-a-user-interface"></a><a name="_core_database_support_with_a_user_interface"></a>Podpora databáze s uživatelským rozhraním

Pokud máte uživatelské rozhraní (například rozhraní příkazového řádku konzoly), aplikace se přímo nakreslí do klientské oblasti okna rámce, nikoli do zobrazení. Taková aplikace nepoužívá `CRecordView`, `CFormView`nebo `CDialog` pro své hlavní uživatelské rozhraní, ale normálně používá `CDialog` pro běžná dialogová okna.

###  <a name="writing-applications-without-documents"></a><a name="_core_writing_applications_without_documents"></a>Psaní aplikací bez dokumentů

Vzhledem k tomu, že Průvodce aplikací nepodporuje vytváření aplikací bez dokumentů, je nutné napsat vlastní třídu odvozenou od `CWinApp`a v případě potřeby také vytvořit třídu `CFrameWnd` nebo `CMDIFrameWnd`. Přepsat `CWinApp::InitInstance` a deklarovat objekt aplikace jako:

```cpp
CYourNameApp theApp;
```

Rozhraní stále poskytuje mechanismus mapování zpráv a mnoho dalších funkcí.

###  <a name="database-support-separate-from-the-user-interface"></a><a name="_core_database_support_separate_from_the_user_interface"></a>Podpora databáze oddělená od uživatelského rozhraní

Některé aplikace nepotřebují žádné uživatelské rozhraní ani pouze minimálně jeden. Předpokládejme například, že píšete:

- Zprostředkující objekt pro přístup k datům, který zavolá jiné aplikace (klienty) pro speciální zpracování dat mezi aplikací a zdrojem dat.

- Aplikace, která zpracovává data bez zásahu uživatele, jako je například aplikace, která přesouvá data z jednoho databázového formátu do jiného, nebo je používá k výpočtům a provádí aktualizace služby Batch.

Vzhledem k tomu, že objekt `CRecordset` nevlastní žádný dokument, pravděpodobně ho budete chtít uložit jako vložený datový člen do vaší třídy aplikace odvozené od `CWinApp`. K alternativám patří:

- Neuchování trvalého objektu `CRecordset`. Konstruktorům třídy sady záznamů můžete předat hodnotu NULL. V takovém případě rozhraní vytvoří dočasný objekt `CDatabase` pomocí informací v `GetDefaultConnect` členské funkci sady záznamů. Toto je nejpravděpodobnější alternativní přístup.

- Vytvoření objektu `CRecordset` globální proměnnou. Tato proměnná by měla být ukazatel na objekt sady záznamů, který vytvoříte dynamicky v přepsání `CWinApp::InitInstance`. Tím se vyhnete pokusu o vytvoření objektu před inicializací rozhraní.

- Použití objektů sady záznamů jako v kontextu dokumentu nebo zobrazení. Vytvořte sady záznamů v členských funkcích objektu aplikace nebo okna s rámečkem.

## <a name="see-also"></a>Viz také

[MFC – databázové třídy](../data/mfc-database-classes-odbc-and-dao.md)
