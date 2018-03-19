---
title: "Zdroj dat: Programové nakonfigurování zdroje dat ODBC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ac5756452a8b1c2d5dbf2f27ac7d3e1a8b069ca2
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Zdroj dat: Programové nakonfigurování zdroje dat ODBC
Toto téma vysvětluje, jak můžete nakonfigurovat připojení ODBC (Open Database) názvy zdrojů dat prostřednictvím kódu programu. To vám dává možnost pro přístup k datům bez vynucení uživateli explicitně zadat názvy zdrojů dat pomocí Správce rozhraní ODBC nebo jiné programy.  
  
 Obvykle se uživatel spustí správce rozhraní ODBC pro vytvoření zdroje dat, pokud tato operace podporuje systém správy přidružené databáze (databázového systému).  
  
 Při vytváření zdroje dat Microsoft Access ODBC prostřednictvím Správce rozhraní ODBC, máte dvě možnosti: můžete vybrat existující soubor .mdb nebo můžete vytvořit nový soubor .mdb. Neexistuje žádný programový způsob vytváření souboru .mdb z vaší aplikace knihovny MFC rozhraní ODBC. Proto pokud vaše aplikace vyžaduje umístění dat do zdroje dat Microsoft Access (.mdb soubor), pravděpodobně budete chtít mít prázdný .mdb soubor, který můžete použít nebo zkopírujte kdykoli budete ho potřebovat.  
  
 Mnoho SŘBD však umožňuje programové vytvoření zdroje dat. Některé zdroje dat udržovat specifikaci adresáře pro databáze. To znamená, adresář je zdroj dat a každá tabulka v rámci zdroj dat je uložen v samostatném souboru (v případě dBASE, každá tabulka je soubor .dbf). Ovladače jiných ODBC databází, jako je například Microsoft Access a SQL Server, vyžadují, že některé určitá kritéria splnit před navázáním zdroj dat. Například pokud používáte ovladač ODBC systému SQL Server, budete muset mít navázat počítače serveru SQL Server.  
  
##  <a name="_core_sqlconfigdatasource_example"></a> Příklad SQLConfigDataSource  
 Následující příklad používá **:: SQLConfigDataSource** funkce rozhraní API ODBC vytvořit nový zdroj dat aplikace Excel volána nový zdroj dat aplikace Excel:  
  
```  
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",   
                   "DSN=New Excel Data Source\0"   
                   "Description=New Excel Data Source\0"   
                   "FileType=Excel\0"   
                   "DataDirectory=C:\\EXCELDIR\0"   
                   "MaxScanRows=20\0");  
```  
  
 Všimněte si, že zdroj dat je ve skutečnosti adresář (C:\EXCELDIR); Tento adresář musí existovat. Ovladač aplikace Excel používá adresáře jako jeho zdroje dat a souborů jako jednotlivé tabulky (jedna tabulka je jeden soubor s příponou XLS).  
  
 Další informace o vytváření tabulek najdete v tématu [zdroj dat: Programové vytvoření tabulky ve zdroji dat rozhraní ODBC](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).  
  
 Tyto informace jsou popsány parametry, které musí být předán **:: SQLConfigDataSource** funkce rozhraní API ODBC. Chcete-li použít **:: SQLConfigDataSource**, musíte zahrnout soubor hlaviček, Odbcinst.h a použít knihovnu Odbcinst.lib. Odbccp32.dll musí být také v cestě v době běhu (nebo Odbcinst.dll pro 16bitové).  
  
 Můžete vytvořit název zdroje dat ODBC pomocí Správce rozhraní ODBC nebo podobného nástroje. V některých případech je však vhodné vytvořit název zdroje dat přímo z vaší aplikace se získat přístup bez nutnosti uživatele k spuštění samostatného nástroje.  
  
 Správce rozhraní ODBC (obvykle instaluje do ovládacích panelů) vytvoří nový zdroj dat vložením položky v registru systému Windows (nebo u 16 bitů, v souboru Odbc.ini). Tento soubor získat požadované informace o zdroji dat se dotazuje správce ovladačů ODBC. Je důležité vědět, jaké informace se musí být umístěny v registru, protože budete muset zadat s volání **:: SQLConfigDataSource**.  
  
 I když tyto informace může zapisovat přímo do registru bez použití **:: SQLConfigDataSource**, jakékoli aplikace, která nemá, tak se spoléhat na aktuální postup, který používá správce ovladačů spravovat jeho data. Pokud pozdější revize pro zachování zdroje dat jiným způsobem záznamů implementuje správce ovladačů ODBC se přeruší všechny aplikace, která používá tento postup. Je většinou vhodné používat funkci rozhraní API, pokud je k dispozici. Váš kód je například přenosný z 16bitové na 32bitové, pokud použijete **:: SQLConfigDataSource** fungovat, protože funkce správně zapisuje do souboru Odbc.ini nebo do registru.  
  
##  <a name="_core_sqlconfigdatasource_parameters"></a> SQLConfigDataSource parametry  
 Následující příklad popisuje parametry **:: SQLConfigDataSource** funkce. Velká část informace jsou převzaty z rozhraní API ODBC *referenční informace pro programátory* dodává s Visual C++ verze 1.5 a novější.  
  
###  <a name="_core_function_prototype"></a> Prototype – funkce  
  
```  
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);  
```  
  
### <a name="remarks"></a>Poznámky  
  
####  <a name="_core_parameters_and_usage"></a> Parametry a použití  
 *hwndParent*  
 Zadané okno jako vlastník všechna dialogová okna Správce ovladačů ODBC nebo konkrétní ovladač ODBC vytvoří od uživatele o nový zdroj dat získat další informace. Pokud `lpszAttributes` parametr neposkytuje dostatek informací, zobrazí se dialogové okno. *HwndParent* může být parametr **NULL**.  
  
 `lpszDriver`  
 Popis ovladače. Toto je název prezentovaný uživatelům, nikoli název fyzického ovladače (DLL).  
  
 `lpszAttributes`  
 Seznam atributů ve tvaru "keyname = hodnota". Tyto řetězce jsou odděleny null konců s dvě po sobě jdoucích null zakončení na konci tohoto seznamu. Tyto atributy se primárně výchozí ovladačem položky, které do registru pro nový zdroj dat. Jeden důležité klíč, který není uvedeno v referenci rozhraní API ODBC pro tuto funkci je "DSN" ("název zdroje dat"), který určuje název nového zdroje dat. Zbývající položky jsou specifické pro ovladač pro nový zdroj dat. Často je nutné zadat všechny položky, protože ovladač můžete vyzvat uživatele s dialogová okna pro nové hodnoty. (Nastavit *hwndParent* k **NULL** způsobí to.) Můžete chtít, aby uživatel nebude vyzván k explicitně výchozí hodnoty.  
  
###### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>Chcete-li zjistit popis ovladač pro parametr lpszDriver pomocí Správce rozhraní ODBC  
  
1.  Spusťte správce rozhraní ODBC.  
  
2.  Klikněte na tlačítko **přidat**.  
  
 To vám dává seznam nainstalovaných ovladačů a jejich popisy. Použít tento popis jako `lpszDriver` parametr. Všimněte si, že používáte celý popis, jako je například "Souborů aplikace Excel (*.XLS)", včetně příponu názvu souboru a kulaté závorky, pokud existují v popisu.  
  
 Jako alternativu můžete zkontrolovat registru (nebo u 16 bitů, soubor Odbcinst.ini), který obsahuje seznam všech ovladačů položek a popisy v klíči registru "Ovladače ODBC" (nebo v části [ODBC – ovladače] v souboru Odbcinst.ini).  
  
 Způsob nalezení "Názvy_klíčů" a hodnoty `lpszAttributes` parametr je prozkoumat soubor Odbc.ini z již nakonfigurovaného zdroje dat (třeba jeden, který je nakonfigurovaný pomocí Správce rozhraní ODBC).  
  
###### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>Najít "Názvy_klíčů" a hodnoty pro parametr lpszAttributes  
  
1.  Spusťte editor registru systému Windows (nebo 16 bitů, otevřete soubor Odbc.ini).  
  
2.  Najít informace zdroje dat ODBC pomocí jedné z následujících akcí:  
  
    -   Pro 32bitové, najít klíč **HKEY_CURRENT_USER\Software\ODBC\ODBC. Zdroje dat INI\ODBC** v levém podokně.  
  
         V pravém podokně jsou uvedené položky ve formátu: "pub: REG_SZ:*<data source name>*", kde  *<data source name>*  je zdroj dat, který již byl konfigurován s požadovaným nastavením pro ovladač, který chcete k použití. Vyberte zdroj dat, který chcete, například SQL Server. Položky následující řetězec "pub:" jsou v pořadí, keyname a hodnoty pro použití v vaší `lpszAttributes` parametr.  
  
    -   Pro 16 bitů, najděte část v souboru Odbc.ini označeny [*\<název zdroje dat >*].  
  
         Následující tohoto řádku řádky jsou ve tvaru "keyname = hodnota". Jedná se přesně položky pro použití v vaší `lpszAttributes` parametr.  
  
 Také můžete chtít zkontrolujte v dokumentaci pro konkrétní ovladač, který chcete použít. Užitečné informace najdete v online nápovědě ovladače, které je přístupné spuštěním Správce rozhraní ODBC. Tyto soubory nápovědy jsou obvykle umístěny v adresáři WINDOWS\SYSTEM pro systém Windows NT, Windows verze 3.1 nebo systému Windows 95.  
  
###### <a name="to-obtain-online-help-for-your-odbc-driver"></a>Získat online nápovědu pro ovladač rozhraní ODBC  
  
1.  Spusťte správce rozhraní ODBC.  
  
2.  Klikněte na tlačítko **přidat**.  
  
3.  Vyberte název ovladače.  
  
4.  Click **OK**.  
  
 Pokud správce rozhraní ODBC zobrazí informace o vytváření nového zdroje dat pro tento konkrétní ovladač, klikněte na tlačítko **pomoci**. Otevře se v souboru nápovědy pro tento konkrétní ovladač, který obvykle obsahuje důležité informace týkající se použití ovladače.  
  
## <a name="see-also"></a>Viz také  
 [Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)