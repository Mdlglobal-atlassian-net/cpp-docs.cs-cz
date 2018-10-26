---
title: 'MFC: Použití databázových tříd bez dokumentů a zobrazení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a4b882ffeed35fb399751eb027bad81ff9007f36
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055187"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC: Použití databázových tříd bez objektů Document a View

Někdy není vhodné používat v rámci architektury dokumentu/zobrazení v databázových aplikacích. Toto téma vysvětluje:

- [Pokud není potřeba používat dokumenty](#_core_when_you_don.92.t_need_documents) například serializace dokumentu.

- [Možnosti Průvodce aplikací](#_core_appwizard_options_for_documents_and_views) pro podporu aplikací bez serializace a související dokument **souboru** příkazy nabídky, jako **nový**, **otevřít** , **Uložit**, a **uložit jako**.

- [Jak pracovat s aplikací, který používá minimální dokument](#_core_applications_with_minimal_documents).

- [Jak strukturovat aplikace bez dokumentů a zobrazení](#_core_applications_with_no_document).

##  <a name="_core_when_you_don.92.t_need_documents"></a> Pokud nepotřebujete dokumentů

Některé aplikace používají odlišné koncept dokumentu. Tyto aplikace obvykle načtení všech nebo většiny souboru z úložiště do paměti **otevřít soubor** příkazu. Aktualizovaný soubor zapisovaly zpět do úložiště najednou pomocí **uložit soubor** nebo **uložit jako** příkazu. To, co uživatel uvidí je soubor datovým souborem.

Některé kategorie aplikací, ale nevyžadují dokumentu. Databázové aplikace pracují z hlediska počtu transakcí. Aplikace vybírá záznamy z databáze a zobrazí uživateli, často jeden po druhém. To, co uživatel uvidí je obvykle jednu aktuální záznam, který může být pouze jednou v paměti.

Pokud vaše aplikace nevyžaduje dokumentu pro ukládání dat, můžete obejít bez některé nebo všechny architektury dokument/zobrazení rozhraní framework. Kolik upustí závisí na přístup, kterému dáváte přednost. Mohli byste:

- Použijte minimální dokument jako místo k uložení připojení ke zdroji dat, ale štítků s normální dokument funkce, jako je serializace. To je užitečné, když má několik zobrazení dat a chcete synchronizovat všechna zobrazení, aktualizovat je všechny najednou a tak dále.

- Použijte okno rámce, do které nakreslíte přímo, namísto použití zobrazení. V tomto případě vynechat dokumentu a uloží data ani připojení dat v objektu oken s rámečkem.

##  <a name="_core_appwizard_options_for_documents_and_views"></a> Možnosti Průvodce aplikací pro dokumenty a zobrazeními

Průvodce aplikací MFC obsahuje celou řadu možností **vyberte Podpora databáze**, které jsou uvedeny v následující tabulce. Pokud používáte Průvodce aplikací knihovny MFC k vytvoření aplikace, tyto možnosti vytvářet aplikace s dokumenty a zobrazeními. Některé možnosti poskytují dokumentů a zobrazení, které vynechat nepotřebné funkce dokumentu. Další informace najdete v tématu [Podpora databáze, Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md).

|Možnost|Zobrazit|Dokument|
|------------|----------|--------------|
|**None**|Odvozené od `CView`.|Poskytuje podporu žádné databáze. Toto je výchozí možnost.<br /><br /> Pokud vyberete **podpora architektury Document/view** možnost [typ aplikace, Průvodce aplikací knihovny MFC](../mfc/reference/application-type-mfc-application-wizard.md) stránky, získáte plnou podporu dokumentu včetně serializace a **nový** , **Otevřít**, **Uložit**, a **uložit jako** příkazy na **souboru** nabídky. Zobrazit [aplikace bez dokumentu](#_core_applications_with_no_document).|
|**Jenom hlavičkové soubory**|Odvozené od `CView`.|Poskytuje základní úroveň podpory databáze pro vaši aplikaci.<br /><br /> Obsahuje Afxdb.h. Přidá knihoven, ale nevytvoří všechny třídy specifické pro databázi. Můžete vytvořit později sady záznamů a použít k prozkoumání a aktualizaci záznamů.|
|**Zobrazení databází bez podpory souborů**|Odvozený z `CRecordView`|Poskytuje podporu dokumentu, ale nepodporuje serializaci. Dokument můžete ukládat sady záznamů a koordinaci více zobrazení; nepodporuje serializaci nebo **nový**, **otevřít**, **Uložit**, a **uložit jako** příkazy. Zobrazit [aplikace s minimálními dokumenty](#_core_applications_with_minimal_documents). Pokud zahrnete zobrazení databáze, musíte zadat zdroj dat.<br /><br /> Obsahuje databázové soubory hlaviček, knihovnách, zobrazení záznamů a záznamů. (K dispozici pouze pro aplikace s **podpora architektury Document/view** možnosti vybrané v [typ aplikace, Průvodce aplikací knihovny MFC](../mfc/reference/application-type-mfc-application-wizard.md) stránky.)|
|**Zobrazení databází s podporou souborů**|Odvozený z `CRecordView`|Poskytuje plnou podporu dokumentu, včetně serializace a související dokument **souboru** příkazů nabídky. Databázové aplikace je obvykle fungují na základě jednotlivé záznamy, nikoli na jednotlivé – soubor základ a proto není nutné serializace. Může však mít speciální použití pro serializaci. Zobrazit [aplikace s minimálními dokumenty](#_core_applications_with_minimal_documents). Pokud zahrnete zobrazení databáze, musíte zadat zdroj dat.<br /><br /> Obsahuje databázové soubory hlaviček, knihovnách, zobrazení záznamů a záznamů. (K dispozici pouze pro aplikace s **podpora architektury Document/view** možnosti vybrané v [typ aplikace, Průvodce aplikací knihovny MFC](../mfc/reference/application-type-mfc-application-wizard.md) stránky.)|

Diskuzi o alternativy k serializaci a alternativní možnosti použití serializace naleznete v tématu [serializace: Serializace vs. Databáze vstupní a výstupní](../mfc/serialization-serialization-vs-database-input-output.md).

##  <a name="_core_applications_with_minimal_documents"></a> Aplikace s minimálními dokumenty

Průvodce aplikací MFC má dvě možnosti, které podporují přístup aplikace založené na formulářích data. Každá možnost vytvoří `CRecordView`-odvozené třídy zobrazení a dokumentu. Se liší v nechají z dokumentu.

###  <a name="_core_a_document_without_file_support"></a> Dokument bez podpory souborů

Vyberte možnost aplikace Průvodce databáze **databáze zobrazení bez podpory souborů** Pokud nepotřebujete serializace dokumentu. Dokument slouží k následujícím účelům:

- Je vhodné místo pro ukládání `CRecordset` objektu.

   Toto použití parallels dokumentu běžné koncepty: dokument uloží data (nebo v tomto případě sadu záznamů) a zobrazení je zobrazení dokumentu.

- Pokud vaše aplikace představuje více zobrazení (například jako zobrazení více záznamů), dokument podporuje koordinaci zobrazení.

   Pokud více zobrazení zobrazit stejná data, můžete použít `CDocument::UpdateAllViews` členskou funkci koordinovat aktualizace pro všechna zobrazení při libovolné zobrazení změní data.

Obvykle použijete tuto možnost pro jednoduché aplikace založené na formulářích. Průvodce aplikací podporuje vhodnou strukturu pro tyto aplikace automaticky.

###  <a name="_core_a_document_with_file_support"></a> Dokument s podporou souborů

Vyberte možnost aplikace Průvodce databáze **databáze zobrazení s podporou souborů** Pokud máte alternativní použití pro související dokument **souboru** příkazů nabídky a serializace dokumentu. Pro přístup k datům je součástí programu, můžete použít dokumentu stejným způsobem, jak je popsáno v [dokumentu bez podpory souborů](#_core_a_document_without_file_support). Možnost serializace dokumentu, můžete použít třeba ke čtení a zápis dokumentu serializované uživatelské profil, který ukládá předvolby uživatele a další užitečné informace. Další informace najdete v článku [serializace: Serializace vs. Databáze vstupní a výstupní](../mfc/serialization-serialization-vs-database-input-output.md).

Průvodce aplikací podporuje tuto možnost, ale je nutné napsat kód, který serializuje dokumentu. Serializované informace Store v dokumentu datové členy.

##  <a name="_core_applications_with_no_document"></a> Aplikace bez dokumentu

Někdy můžete chtít napsat aplikaci, která nepoužívá dokumenty a zobrazení. Bez dokumentů, ukládat data (například `CRecordset` objektu) ve vaší třídy oken s rámečkem nebo ve třídě aplikace. Veškeré další požadavky závisí na tom, jestli aplikace představuje uživatelské rozhraní.

###  <a name="_core_database_support_with_a_user_interface"></a> Podpora databáze s uživatelským rozhraním

Pokud máte uživatelské rozhraní (jiné než, například rozhraní příkazového řádku konzoly), vaše aplikace kreslení přímo do klientské oblasti okna rámce, nikoli do zobrazení. Takovou aplikaci nepoužívá `CRecordView`, `CFormView`, nebo `CDialog` pro jeho hlavní uživatelské rozhraní, ale obvykle použít `CDialog` pro běžná dialogová okna.

###  <a name="_core_writing_applications_without_documents"></a> Psaní aplikací bez dokumentů

Protože Průvodce aplikací nepodporuje vytváření aplikací bez dokumenty, musíte napsat vlastní `CWinApp`-odvozené třídy a v případě potřeby také vytvořit `CFrameWnd` nebo `CMDIFrameWnd` třídy. Přepsat `CWinApp::InitInstance` a deklarovat objekt aplikace jako:

```cpp
CYourNameApp theApp;
```

Architektura dodává stále mechanismu mapování zpráv a mnoho dalších funkcí.

###  <a name="_core_database_support_separate_from_the_user_interface"></a> Podpora databáze oddělená od uživatelského rozhraní

Některé aplikace potřebují žádné uživatelské rozhraní nebo pouze minimální verzi. Předpokládejme například, že píšete:

- Jiné aplikace (klienty) vyžadují zvláštní zpracování dat mezi aplikací a zdroj dat objekt zprostředkující přístup k datům.

- Aplikace, která zpracovává data bez zásahu uživatele, například aplikace, který přesouvá data z jednoho databázového formátu do jiného, nebo ten, který provede výpočty a provádí dávkové aktualizace.

Protože vlastní žádný dokument `CRecordset` objektu, budete pravděpodobně chtít uložit jako vložený datový člen v vaše `CWinApp`-odvozené třídy aplikace. Mezi ně patří:

- Není udržování trvalou `CRecordset` objektu. Konstruktorům třídy sady záznamů můžete předat hodnotu NULL. V takovém případě rozhraní vytvoří dočasnou `CDatabase` pomocí informací v sadě záznamů `GetDefaultConnect` členskou funkci. Toto je nejpravděpodobnější alternativním přístupem.

- Provádění `CRecordset` objektu globální proměnné. Tato proměnná musí být ukazatel na objekt sady záznamů, který vytvoříte dynamicky ve vašich `CWinApp::InitInstance` přepsat. Tím se vyhnete pokusu o vytvoření objektu před dokončením inicializace rozhraní framework.

- Použití objektů sady záznamů, stejně jako v rámci dokumentu, nebo v náhledu. Vytvoření sady záznamů v člen funkce svou aplikaci nebo objekty oken s rámečkem.

## <a name="see-also"></a>Viz také

[MFC – databázové třídy](../data/mfc-database-classes-odbc-and-dao.md)