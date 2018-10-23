---
title: Výstupní parametry | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4a17ff7e6e78b21267b71ba495ba10a98e29cfe7
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808847"
---
# <a name="output-parameters"></a>Výstupní parametry

Volání uložené procedury je podobná spuštění příkazu SQL. Hlavní rozdíl je, že uložených procedur použijte výstupní parametry (nebo "výstupní parametry") a návratových hodnot.

Těmito uloženou proceduru, první '? 'je návratová hodnota (telefon) a druhá'?' je vstupní parametr (název):

```  
DEFINE_COMMAND(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }")  
```  

Zadat vstupní a výstupní parametry v mapě parametr:

```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)  
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter
END_PARAM_MAP()  
```  

Ke zpracování potřeba aplikace výstupu vráceného z uložené procedury. Různé technologie OLE DB – zprostředkovatelé vrátit výstupní parametry a návratové hodnoty v různých časech během zpracování výsledku. Zprostředkovatel Microsoft OLE DB pro SQL Server (SQLOLEDB) není třeba výstupní parametry a návratové kódy až po příjemce načte nebo zruší sady výsledků vrácené procedurou. uložené. Výstup se vrací v posledním TDS paketu ze serveru.

## <a name="row-count"></a>Počet řádků

Pokud používáte ke spuštění uložené procedury, která má výstupní parametry šablony příjemce technologie OLE DB, počet řádků není nastavená, dokud ho neukončíte sadu řádků.

Představte si třeba uložené procedury s sady řádků a výstupním parametrem:

```sql
create procedure sp_test
   @_rowcount integer output
as
   select top 50 * from test
   @_rowcount = @@rowcount
return 0
```  

\@_Rowcount výstupní zprávy, kolik řádků vrácených z tabulky testu. Tuto uloženou proceduru však omezuje počet řádků na 50. Například pokud byly nějaké 100 řádků v testu, rowcount by 50 (protože je tento kód načte jenom prvních 50 řádků). Pokud byly nějaké pouze 30 řádky v tabulce, by rowcount 30. Nezapomeňte volat `Close` nebo `CloseAll` k naplnění výstupní před načíst jeho hodnotu.

## <a name="see-also"></a>Viz také

[Použití uložených procedur](../../data/oledb/using-stored-procedures.md)