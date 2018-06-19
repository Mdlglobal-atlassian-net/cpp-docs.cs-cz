---
title: Průvodce příjemcem knihovny MFC rozhraní ODBC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.class.mfc.consumer.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC ODBC Consumer Wizard
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c8a707df6878cd0031cb2ec9b06285e568503992
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371421"
---
# <a name="mfc-odbc-consumer-wizard"></a>Průvodce příjemcem knihovny MFC ODBC
Sem vložte "Search" shrnutí výsledků.  
  
 Tento průvodce nastavuje třídu sady záznamů rozhraní ODBC a datové vazby potřebné pro přístup ke zdroji zadaná data.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Zdroj dat**  
 **Zdroj dat** tlačítko umožňuje nastavit zadaný zdroj dat pomocí zadaný ovladač ODBC. Další informace o soubory zdroje dat (DSN) najdete v tématu [souborových zdrojů dat](https://msdn.microsoft.com/library/ms715401.aspx) v sadě SDK ODBC. **Vybrat zdroj dat** dialogové okno obsahuje dvě karty:  
  
-   **Soubor zdroje dat** karta: **Hledat v** pole určuje adresář, do kterého chcete vyberte soubory, které má být použit jako zdroje dat. Výchozí hodnota je \Program Files\Common Files\ODBC\Data zdroje. V hlavním seznamu se zobrazí existující soubor zdroje dat. (soubory DSN). Můžete buď nastavení zdroje dat před současně pomocí **souborové DSN** na kartě [správce zdrojů dat ODBC](https://msdn.microsoft.com/library/ms714024.aspx), nebo vytvořit nové pomocí tohoto dialogového okna.  
  
     Chcete-li vytvořit nový soubor zdroje dat z tohoto dialogového okna, klikněte na tlačítko `New` k zadání názvu DSN; **vytvořit nový zdroj dat** zobrazí se dialogové okno. V **vytvořit nový zdroj dat** dialogovém okně vyberte příslušný ovladač a klikněte na tlačítko `Next`; klikněte na tlačítko **Procházet**a vyberte název souboru, který se použije jako zdroj dat (budete muset vybrat "všechny soubory. zobrazení bez DSN soubory, jako jsou soubory XLS); Klikněte na tlačítko `Next`a potom klikněte na **Dokončit**. (Pokud jste vybrali soubor názvu DSN, zobrazí se ovladačem dialogového okna, jako je například "Nastavení rozhraní ODBC Microsoft Excel," který převede soubor názvu DSN.)  
  
    > [!NOTE]
    >  Můžete také vytvořit nový zdroj dat souboru předem pomocí Správce zdrojů dat ODBC. Z **spustit** nabídce vyberte možnost **nastavení**, **ovládací panely**, **nástroje pro správu**, **datové zdroje (ODBC)** a potom **správce zdrojů dat ODBC**.  
  
     **Název DSN** pole můžete zadat název pro zdroj dat souboru. Je nutné zajistit, že název DSN končí příslušnou příponu souboru, například .xls souborů aplikace Excel nebo .mdb pro přístup k souborům.  
  
     Další informace o názvech zdrojů dat najdete v tématu [souborových zdrojů dat](https://msdn.microsoft.com/library/ms715401.aspx) v sadě SDK ODBC.  
  
-   **Počítač zdroj dat** karta: Tato karta obsahuje systém a zdroje dat uživatele. Zdroje dat uživatele jsou specifické pro uživatele na tomto počítači. Systémové zdroje dat lze všichni uživatelé v tomto počítači nebo na službě. V tématu [počítač zdroje dat](https://msdn.microsoft.com/library/ms710952.aspx) v sadě SDK rozhraní ODBC  
  
 Další informace o zdroje dat ODBC, najdete v části [zdroje dat](https://msdn.microsoft.com/library/ms711688.aspx) v sadě SDK ODBC.  
  
 Klikněte na tlačítko **OK** ukončíte. **Vyberte objekt databáze** zobrazí se dialogové okno. Z tohoto dialogového vyberte tabulku nebo zobrazení, použijete k příjemce. Všimněte si, že můžete vybrat více tabulek a zobrazení tak, že podržíte klávesu řízení při kliknutí na položky.  
  
 **– Třída**  
 Název třídy příjemce, ve výchozím nastavení na základě názvu zdroje dat souboru nebo počítač, který jste vybrali.  
  
 **soubor h**  
 Název souboru záhlaví třídy příjemce ve výchozím nastavení na základě názvu zdroje dat souboru nebo počítač, který jste vybrali.  
  
 **souboru**  
 Název souboru implementace třídy příjemce ve výchozím nastavení na základě názvu zdroje dat souboru nebo počítač, který jste vybrali.  
  
 **Typ**  
 Určuje, zda je záznamů dynamická sada (výchozí) nebo snímek.  
  
-   **Dynamická sada**: Určuje, že je dynamická sada záznamů. Dynamická sada je výsledkem dotazu, který poskytuje indexované zobrazení na data dotazované databázi. Dynamická sada pouze celočíselný index pro původní data ukládá do mezipaměti, a proto nabízí a výkonu získat přes snímek. Index odkazuje přímo na všech vybraných záznamech výsledkem dotazu a určuje, pokud je odebrat záznam. Máte také přístup k aktualizované informace v záznamech předmětem dotazu. Toto nastavení je výchozí.  
  
-   **Snímek**: Určuje, že je záznamů snímku. Snímek je výsledek dotazu a zobrazení do databáze v jednom bodě v čase. Všechny záznamy nalezené v důsledku dotaz jsou v mezipaměti, takže se nezobrazí žádné změny původní záznamy.  
  
 **Vytvoření vazby všechny sloupce**  
 Určuje, zda jsou vázány všechny sloupce ve vybrané tabulce. Pokud zaškrtnete toto políčko (výchozí), jsou všechny sloupce vázány; Pokud toto políčko nezaškrtnete, žádné sloupce je vázána a je třeba svázat ručně ve třídě sady záznamů.  
  
## <a name="see-also"></a>Viz také  
 [Knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)

