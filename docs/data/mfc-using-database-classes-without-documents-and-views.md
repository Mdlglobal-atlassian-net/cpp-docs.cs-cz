---
title: 'MFC: Použití databázových tříd bez objektů Document a View | Microsoft Docs'
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
ms.openlocfilehash: ba2e59b53524975f87e4ad7ffe99b9a4a3cc870d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093893"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC: Použití databázových tříd bez objektů Document a View
V některých případech nemusí chtít použít rozhraní framework document/view – architektura v databázových aplikacích. Toto téma vysvětluje:  
  
-   [Pokud není potřeba použít dokumenty](#_core_when_you_don.92.t_need_documents) například dokument serializace.  
  
-   [Možnosti Průvodce aplikací](#_core_appwizard_options_for_documents_and_views) pro podporu aplikací bez serializace a bez souvisejících s dokumenty **soubor** nabídky příkazy, jako **nový**, **otevřete** , **Uložit**, a **uložit jako**.  
  
-   [Jak pracovat s aplikací, která používá minimální dokument](#_core_applications_with_minimal_documents).  
  
-   [Postup struktury aplikace bez dokumentu nebo zobrazení](#_core_applications_with_no_document).  
  
##  <a name="_core_when_you_don.92.t_need_documents"></a> Pokud nepotřebujete dokumenty  
 Některé aplikace mají odlišný koncept dokumentu. Tyto aplikace obvykle načtou všechny nebo většinu souborů z úložiště do paměti **otevřít soubor** příkaz. Zapíší aktualizovaný soubor zpět do úložiště najednou pomocí **uložit soubor** nebo **uložit jako** příkaz. To, co uživatel uvidí je datový soubor.  
  
 Některé kategorie aplikací, ale nevyžadují dokumentu. Databáze aplikace pracují v rámci transakce. Aplikace vybere záznamy z databáze a k jejich zobrazení pro uživatele, často jeden po druhém. To, co uživatel uvidí je obvykle jeden aktuální záznam, který může být jediný v paměti.  
  
 Pokud aplikace nevyžaduje dokumentu pro ukládání dat, můžete se obejít bez některých nebo všech rozhraní framework document/view – architektura. Kolik obejít bez závisí na přístupu, kterému dáváte přednost. Vám může:  
  
-   Použijte minimální dokument jako místo uložení připojení ke zdroji dat, ale obejít bez normální dokumentu funkce jako je například serializace. To je užitečné, když má několik zobrazení dat a chcete synchronizovat všechna zobrazení, aktualizovat je všechny najednou, a tak dále.  
  
-   Použijte okno rámce, do kterého jste kreslení přímo, namísto pomocí zobrazení. V takovém případě vynechejte dokumentu a ukládat data ani připojení dat v objektu oken s rámečkem.  
  
##  <a name="_core_appwizard_options_for_documents_and_views"></a> Možnosti Průvodce aplikací pro dokumenty a zobrazeními  
 Průvodce aplikací MFC má několik možností v **vyberte podpory databáze**, které jsou uvedeny v následující tabulce. Pokud používáte Průvodce aplikací MFC vytvořit aplikaci, všechny tyto možnosti vytvořit aplikace s dokumenty a zobrazeními. Některé možnosti poskytují dokumenty a zobrazení, která vynechají nepotřebné funkce dokumentu. Další informace najdete v tématu [Podpora databáze, Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md).  
  
|Možnost|Zobrazit|Dokument|  
|------------|----------|--------------|  
|**None**|Odvozené z `CView`.|Poskytuje podporu žádné databáze. Toto je výchozí možnost.<br /><br /> Pokud jste vybrali **Document/view – architektura podporu** možnost [typu aplikace, Průvodce aplikací knihovny MFC](../mfc/reference/application-type-mfc-application-wizard.md) , dostanete úplnou podporu dokumentu včetně serializace a `New`,  **Otevřete**, **Uložit**, a **uložit jako** příkazy **souboru** nabídky. V tématu [aplikace bez dokumentu](#_core_applications_with_no_document).|  
|**Pouze soubory hlaviček**|Odvozené z `CView`.|Poskytuje základní úroveň podpory databáze pro vaši aplikaci.<br /><br /> Obsahuje Afxdb.h. Přidá knihovny DLL, ale nevytvoří žádné třídy specifické pro databázi. Můžete vytvořit sady záznamů později a použít ji ke zkoumání a aktualizaci záznamů.|  
|**Zobrazení databáze bez podpory souborů**|Odvozené od `CRecordView`|Poskytuje podporu dokumentu, ale nepodporuje serializaci. Dokument můžete ukládat sady záznamů a koordinaci více zobrazení; nepodporuje serializaci nebo `New`, **otevřete**, **Uložit**, a **uložit jako** příkazy. V tématu [aplikace s minimálními dokumenty](#_core_applications_with_minimal_documents). Pokud zahrnete zobrazení databáze, musíte zadat zdroj dat.<br /><br /> Zahrnuje databázové soubory hlaviček, knihovny DLL, zobrazení záznamů a sadě záznamů. (K dispozici pouze pro aplikace s **Document/view – architektura podporu** možnost na [typu aplikace, Průvodce aplikací knihovny MFC](../mfc/reference/application-type-mfc-application-wizard.md) stránky.)|  
|**Zobrazení databáze s podporou souboru**|Odvozené od `CRecordView`|Poskytuje podporu celého dokumentu, včetně serializace a související dokumentu **souboru** příkazy nabídky. Databázové aplikace se obvykle fungují na základě na záznam, místo na po souborech a tak nemusí serializace. Můžete však mít zvláštní použití pro serializaci. V tématu [aplikace s minimálními dokumenty](#_core_applications_with_minimal_documents). Pokud zahrnete zobrazení databáze, musíte zadat zdroj dat.<br /><br /> Zahrnuje databázové soubory hlaviček, knihovny DLL, zobrazení záznamů a sadě záznamů. (K dispozici pouze pro aplikace s **Document/view – architektura podporu** možnost na [typu aplikace, Průvodce aplikací knihovny MFC](../mfc/reference/application-type-mfc-application-wizard.md) stránky.)|  
  
 Informace alternativami pro serializaci a alternativní používá pro serializaci, naleznete v [serializace: Serializace vs. Databáze vstupu a výstupu](../mfc/serialization-serialization-vs-database-input-output.md).  
  
##  <a name="_core_applications_with_minimal_documents"></a> Aplikace s minimálními dokumenty  
 Průvodce aplikací MFC má dvě možnosti, které podporují přístup k aplikacím na základě formulářů data. Každá možnost vytvoří `CRecordView`-odvozené třídy zobrazení a dokumentu. Liší se vynechají z dokumentu.  
  
###  <a name="_core_a_document_without_file_support"></a> Dokument bez podpory souboru  
 Vyberte možnost Průvodce aplikace databáze **databáze zobrazení bez podpory souboru** Pokud nepotřebujete serializaci dokumentu. Dokument slouží k následujícím účelům:  
  
-   Je vhodné místo pro ukládání `CRecordset` objektu.  
  
     Toto použití paralelní s koncepty běžného dokument: dokument uloží data (nebo v tomto případě sadu záznamů) a zobrazení je zobrazení dokumentu.  
  
-   Pokud aplikace představuje více zobrazení (například více zobrazení záznamů), dokument podporuje koordinaci zobrazení.  
  
     Pokud více zobrazení zobrazit stejná data, můžete použít `CDocument::UpdateAllViews` – členská funkce pro koordinaci aktualizací u všech zobrazení, když se změní všechna zobrazení, data.  
  
 Tuto možnost obvykle použijete pro jednoduché aplikace založené na formulářích. Průvodce aplikace podporuje vhodnou strukturu pro tyto aplikace automaticky.  
  
###  <a name="_core_a_document_with_file_support"></a> Dokument se podpora souborů  
 Vyberte možnost Průvodce aplikace databáze **databáze zobrazení s podporou souboru** Pokud máte alternativní použití pro související dokumentu **souboru** příkazy nabídky a serializace dokumentu. Pro přístup k datům část vašeho programu, můžete použít dokument stejným způsobem, jak je popsáno v [dokument bez podpory souboru](#_core_a_document_without_file_support). Možnost serializace dokumentu, můžete použít například ke čtení a zápisu dokument serializované uživatelské profil, který ukládá uživatelské předvolby a další užitečné informace. Další nápady najdete v části [serializace: Serializace vs. Databáze vstupu a výstupu](../mfc/serialization-serialization-vs-database-input-output.md).  
  
 Průvodce aplikace podporuje tuto možnost, ale musíte napsat kód, který serializuje dokumentu. Uložte serializované informace v dokumentu datových členů.  
  
##  <a name="_core_applications_with_no_document"></a> Aplikace bez dokumentu  
 V některých případech můžete chtít zápisu aplikace, která nepoužívá dokumenty a zobrazení. Bez dokumentů, ukládat data (například `CRecordset` objektu) ve vaší třídy oken s rámečkem nebo ve třídě aplikace. Veškeré další požadavky závisí na tom, jestli aplikace uvede uživatelské rozhraní.  
  
###  <a name="_core_database_support_with_a_user_interface"></a> Podpora databáze s uživatelským rozhraním  
 Pokud máte uživatelské rozhraní (jiné než například konzole rozhraní příkazového řádku), vaše aplikace nevykresluje přímo do okna rámce klientské oblasti spíše než do zobrazení. Takové aplikace nepoužívá `CRecordView`, `CFormView`, nebo `CDialog` jeho hlavní uživatelské rozhraní, ale normálně používat `CDialog` pro běžná dialogová okna.  
  
###  <a name="_core_writing_applications_without_documents"></a> Psaní aplikací bez dokumentů  
 Jelikož průvodce aplikace nepodporuje vytváření aplikací bez dokumentů, musíte napsat vlastní `CWinApp`-odvozené třídy a v případě potřeby také vytvořit `CFrameWnd` nebo `CMDIFrameWnd` třídy. Přepsání `CWinApp::InitInstance` a deklarovat objekt aplikace jako:  
  
```  
CYourNameApp theApp;  
```  
  
 Rozhraní framework stále poskytuje mechanismus map zpráv a řadu dalších funkcí.  
  
###  <a name="_core_database_support_separate_from_the_user_interface"></a> Podpora databáze oddělená od uživatelského rozhraní  
 Některé aplikace potřebují žádné uživatelské rozhraní nebo pouze minimální jeden. Předpokládejme například, že vytváříte:  
  
-   Jiné aplikace (klientů) volání pro zvláštní zpracování dat mezi aplikací a zdroj dat objekt zprostředkující přístup k datům.  
  
-   Aplikace, která zpracovává data bez zásahu uživatele, například aplikace, které přesouvá data z jednoho formátu databáze do jiné nebo ten, který provede výpočty a provádí dávková aktualizace.  
  
 Protože žádný dokument nevlastní `CRecordset` objektu, budete ho zřejmě chtít uložit jako člena vložená data ve vaší `CWinApp`-odvozené třídy aplikace. Mezi ně patří:  
  
-   Aby nebyl trvalou `CRecordset` objektu vůbec. Abyste mohli předávat **NULL** konstruktorům třídy sady záznamů. V takovém případě rozhraní framework vytvoří dočasný `CDatabase` objektu pomocí informací v sadě záznamů `GetDefaultConnect` – členská funkce. Toto je nejpravděpodobnější alternativní přístup.  
  
-   Provádění `CRecordset` objektu globální proměnné. Tato proměnná by měla být ukazatel na objekt sady záznamů, který vytvoříte dynamicky ve vaší `CWinApp::InitInstance` přepsat. Tím je zabráněno pokusu o sestavení objektu před inicializací rozhraní.  
  
-   Použití objektů sady záznamů, stejně jako v kontextu dokumentu nebo zobrazení. Vytvoření sady záznamů v člen funkce vaší aplikace nebo pro objekty oken s rámečkem.  
  
## <a name="see-also"></a>Viz také  
 [MFC – databázové třídy](../data/mfc-database-classes-odbc-and-dao.md)