---
title: 'Zdroj dat: Programové nakonfigurování zdroje dat ODBC | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
f1_keywords:
- SQLConfigDataSource
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 36f8233d7d3683a885fc0f38468ad5a7b9b59c57
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030765"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Zdroj dat: Programové nakonfigurování zdroje dat ODBC

Toto téma vysvětluje, jak nakonfigurovat názvy zdroje dat připojení ODBC (Open Database) prostřednictvím kódu programu. To vám nabídne flexibilitu pro přístup k datům bez explicitního uživatelského specifikování názvů zdrojů dat explicitně pomocí Správce rozhraní ODBC nebo jiných programů.  
  
Obvykle uživatel spustí správce rozhraní ODBC k vytvoření zdroje dat, je-li tuto operaci podporuje systém správy přidružená databáze (DBMS).  
  
Při vytváření zdroje dat Microsoft Access ODBC přes správce rozhraní ODBC, budete mít dvě možnosti: můžete vybrat existující soubor .mdb soubor nebo můžete vytvořit nový soubor .mdb. Neexistuje žádný programový způsob vytváření souboru .mdb z vaší aplikace knihovny MFC rozhraní ODBC. Proto pokud vaše aplikace vyžaduje umístění dat ke zdroji dat Microsoft Access (soubor .mdb), pravděpodobně budete chtít mít prázdný .mdb soubor, který můžete použít nebo zkopírovat vždy, když je potřebujete.  
  
Nicméně mnoho DBMS umožňuje programové vytvoření zdroje dat. Některé zdroje dat zachovávají adresářovou specifikaci pro databáze. To znamená, že adresář představuje zdroj dat a každá tabulka v rámci zdroje dat je uložena v samostatném souboru (v případě dBASE, každá tabulka je soubor s příponou .dbf). Ovladače jiných ODBC databází, jako je například aplikace Microsoft Access a SQL Server, vyžadují, některých specifických kritérií splnit, předtím, než zdroj dat je možné navázat. Například při použití ovladač ODBC systému SQL Server, budete muset zavedli počítače systému SQL Server.  
  
##  <a name="_core_sqlconfigdatasource_example"></a> Příklad SQLConfigDataSource  

V následujícím příkladu `::SQLConfigDataSource` funkce ODBC API k vytvoření nového zdroje dat aplikace Excel názvem New Excel Data Source:  
  
```  
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",   
                   "DSN=New Excel Data Source\0"   
                   "Description=New Excel Data Source\0"   
                   "FileType=Excel\0"   
                   "DataDirectory=C:\\EXCELDIR\0"   
                   "MaxScanRows=20\0");  
```  
  
Všimněte si, že zdroj dat je ve skutečnosti adresář (C:\EXCELDIR); Tento adresář musí existovat. Ovladač aplikace Excel používá adresáře jako své zdroje dat a soubory jako jednotlivé tabulky (jedna tabulka na jeden .xls soubor).  
  
Další informace o vytváření tabulek naleznete v tématu [zdroj dat: Programové vytvoření tabulky ve zdroji dat rozhraní ODBC](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).  
  
Následující informace popisují parametry, které je potřeba předat `::SQLConfigDataSource` funkce ODBC API. Chcete-li použít `::SQLConfigDataSource`, je nutné zahrnout hlavičku souboru Odbcinst.h a použít importovanou knihovnu Odbcinst.lib. Navíc Odbccp32.dll musí být v cestě v době běhu (nebo DLL knihovna Odbcinst.dll pro 16 bitů).  
  
Můžete vytvořit název zdroje dat ODBC přes správce rozhraní ODBC nebo podobného nástroje. Někdy je však žádoucí vytvořit název zdroje dat přímo z vaší aplikace k získání přístupu, aniž by uživatel spouštěl samostatný nástroj.  
  
Správce rozhraní ODBC (obvykle nainstalován v Ovládacích panelech) vytváří nový zdroj dat vložením položky do registru Windows (nebo u 16bitových verzí do souboru Odbc.ini). Tento soubor a získat požadované informace o zdroji dat se dotazuje správce ovladačů ODBC. Je důležité vědět, jaké informace musí být umístěny v registru, protože budete muset zadat volání `::SQLConfigDataSource`.  
  
I když tyto informace může být přímo zapsána do registru bez použití `::SQLConfigDataSource`, všechny aplikace, která tak učiní, se spoléhá na současnou techniku, kterou správce ovladačů používá k získání svých dat. Pokud bude pozdější změna správce ovladačů ODBC implementovat zachování záznamů o zdrojích dat jiným způsobem, všechny aplikace používající tuto techniku se přeruší. Je obecně vhodné použít funkci rozhraní API, pokud je k dispozici. Váš kód je třeba přenosný z 16bitového na 32bitový, pokud použijete `::SQLConfigDataSource` fungovat, protože funkce správně zapisuje do souboru Odbc.ini nebo do registru.  
  
##  <a name="_core_sqlconfigdatasource_parameters"></a> Parametry SQLConfigDataSource  

Následující příklad popisuje parametry `::SQLConfigDataSource` funkce. Většina informací je převzata z rozhraní ODBC API *referenční informace pro programátory* dodávané s Visual C++ verze 1.5 a novější.  
  
###  <a name="_core_function_prototype"></a> Prototyp funkce  
  
```  
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);  
```  
  
### <a name="remarks"></a>Poznámky  
  
####  <a name="_core_parameters_and_usage"></a> Parametry a použití  

*hwndParent*<br/>
Okno, specifikované jako vlastník libovolného dialogového okna, že k získání potřebných informací od uživatele o nový zdroj dat vytvoří správcem ovladačů rozhraní ODBC nebo konkrétní ovladač ODBC. Pokud *lpszAttributes* parametr neposkytuje dostatek informací, zobrazí se dialogové okno. *HwndParent* parametr může mít hodnotu NULL.  
  
*lpszDriver*<br/>
Popis ovladače. Toto je název prezentovaný uživatelům, nikoli fyzický název ovladače (DLL).  
  
*lpszAttributes*<br/>
Seznam atributů ve formě "Název_klíče = hodnota". Tyto řetězce jsou odděleny znakem null a zakončeny dvěma po sobě jdoucí znaky "null" na konci seznamu. Tyto atributy jsou primárně výchozí specifický ovladač položek, které jsou předávány do registrů pro nový zdroj dat. Jeden důležitý klíč, který není zmíněn v referenční dokumentaci rozhraní API ODBC pro tuto funkci je "DSN" ("název zdroje dat"), který určuje název nového zdroje dat. Zbývající položky jsou specifické pro ovladač pro nový zdroj dat. Není často nutné zadat všechny položky, protože ovladač může vyzvat uživatele s dialogová okna pro nové hodnoty. (Nastavit *hwndParent* na hodnotu NULL způsobí to.) Můžete explicitně poskytnout výchozí hodnoty tak, aby se uživateli nezobrazí výzva.  
  
###### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>Určení popisu ovladače pro parametr lpszDriver pomocí Správce rozhraní ODBC  
  
1. Spusťte správce rozhraní ODBC.  
  
1. Klikněte na tlačítko **přidat**.  
  
To poskytuje seznam nainstalovaných ovladačů a jejich popisy. Použijte tento popis jako *lpszDriver* parametru. Všimněte si, že používáte celý popis, jako je například "Souborů aplikace Excel (*.XLS)", včetně příponu názvu souboru a kulaté závorky, pokud existují v popisu.  
  
Jako alternativu můžete ověřit registr (nebo u 16bitové verze soubor Odbcinst.ini), který obsahuje seznam všech ovladačů položky a popisy v klíči registru "Ovladače rozhraní ODBC" (nebo část [ovladače rozhraní ODBC] v souboru Odbcinst.ini).  
  
Jeden ze způsobů, jak najít názvy klíčů a hodnot pro *lpszAttributes* parametr je prozkoumat soubor Odbc.ini pro již nakonfigurovaný zdroj, (např. ten, který byl nakonfigurován správcem rozhraní ODBC).  
  
###### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>K vyhledání názvu klíčů a hodnot pro parametr lpszAttributes  
  
1. Spusťte editor registru Windows (nebo u 16bitové verze otevřete soubor Odbc.ini).  
  
1. Najdete informace zdroje dat ODBC pomocí jedné z následujících akcí:  
  
    -   U 32bitové verze vyhledejte klíč **HKEY_CURRENT_USER\Software\ODBC\ODBC. Zdroje dat INI\ODBC** v levém podokně.  
  
         V pravém podokně jsou uvedeny položky ve formátu: "pub: REG_SZ:*<data source name>*", kde *<data source name>* je zdroj dat, která je už nakonfigurovaná s požadovaným nastavením ovladače určené pro instalaci k použití. Vyberte zdroj dat, které potřebujete, třeba SQL Server. Položky následující za řetězcem "pub:" jsou v pořadí, název klíče a hodnoty pro použití v vaše *lpszAttributes* parametru.  
  
    -   U 16bitové verze, najděte část do souboru Odbc.ini označeny [*\<název zdroje dat >*].  
  
         Řádky následující tento řádek jsou ve tvaru "Název_klíče = hodnota". Jedná se přesně o položky ve vaší *lpszAttributes* parametru.  
  
Můžete také prozkoumat dokumentaci pro konkrétní ovladač, který se chystáte používat. Užitečné informace najdete v online nápovědě pro ovladač, která je přístupná po spuštění Správce rozhraní ODBC. Tyto soubory nápovědy jsou obvykle umístěny v adresáři WINDOWS\SYSTEM u systému Windows NT, Windows 3.1 nebo Windows 95.  
  
###### <a name="to-obtain-online-help-for-your-odbc-driver"></a>Získání online nápovědy pro ovladač rozhraní ODBC  
  
1. Spusťte správce rozhraní ODBC.  
  
1. Klikněte na tlačítko **přidat**.  
  
1. Vyberte název ovladače.  
  
1. Klikněte na tlačítko **OK**.  
  
Jakmile správce rozhraní ODBC zobrazí informace o vytváření nového zdroje dat pro tento konkrétní ovladač, klepněte na tlačítko **pomáhají**. Otevře se v souboru nápovědy pro tento konkrétní ovladač, který obvykle obsahuje důležité informace týkající se použití ovladače.  
  
## <a name="see-also"></a>Viz také  

[Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)