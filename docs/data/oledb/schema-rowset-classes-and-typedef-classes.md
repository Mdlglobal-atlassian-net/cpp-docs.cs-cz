---
title: "Třídy sady řádků schématu a definiční třídy typů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.templates.ole
dev_langs: C++
helpviewer_keywords: schema rowsets, classes
ms.assetid: 4bd881b3-26ca-4bdb-9226-d67560864f29
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 27cb8085711ae9756b9bb5c1042bbe5475619025
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="schema-rowset-classes-and-typedef-classes"></a>Třídy sady řádků schématu a definiční třídy typů
Schéma je kolekce databázové objekty, které jsou ve vlastnictví, nebo byly vytvořeny, konkrétním uživatelem. Katalog může obsahovat jeden nebo více schémat, ale musí obsahovat vždy schéma názvem INFORMATION_SCHEMA, která obsahuje zobrazení a domén informace o schématu. Informace o schématu v OLE DB se načítají pomocí předdefinované sady řádků schématu a obsahuje typy, tabulky, sloupce, indexy, zobrazení, kontrolní výrazy a omezení, statistiky, znakových sad, kolace a domén.  
  
 Sady řádků schématu jsou předdefinované sady řádků představující metadat. Schéma sad řádků se obecně používají ve dynamické programování, kde není znám struktura databáze v době kompilace. Tyto sady řádků schématu můžete použít k získání informací o databázi v době běhu.  
  
 Použijte definiční třídy typů k vytváření instancí sady řádků schématu. Odpovídající typedef a třídy sady řádků schématu jsou uvedeny níže. Je třeba volat [CRestrictions::Open](../../data/oledb/crestrictions-open.md) po vytvoření instance sady řádků schématu. Tato metoda vrátí sadu výsledků na základě omezení, které zadáte. V tématu [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) informace o omezení sloupce spojené s každou sada řádků schématu.  
  
 Následující tabulka zobrazuje každou OLE DB sada řádků schématu a odpovídající – třída definice typedef šablony technologie OLE DB a informace o třída.  
  
|Sada řádků schématu OLE DB|– Třída definice TypeDef|Informace o – třída|  
|--------------------------|-------------------|----------------|  
|[KONTROLNÍ VÝRAZY](https://msdn.microsoft.com/en-us/library/ms719776.aspx)|[CAssertions](../../data/oledb/cassertions-cassertioninfo.md)|[CAssertionInfo](../../data/oledb/cassertions-cassertioninfo.md)|  
|[KATALOGY](https://msdn.microsoft.com/en-us/library/ms721241.aspx)|[CCatalogs](../../data/oledb/ccatalogs-ccataloginfo.md)|[CCatalogInfo](../../data/oledb/ccatalogs-ccataloginfo.md)|  
|[CHARACTER_SETS](https://msdn.microsoft.com/en-us/library/ms722638.aspx)|[CCharacterSets](../../data/oledb/ccharactersets-ccharactersetinfo.md)|[CCharacterSetInfo](../../data/oledb/ccharactersets-ccharactersetinfo.md)|  
|[KOLACE](https://msdn.microsoft.com/en-us/library/ms715783.aspx)|[CCollations](../../data/oledb/ccollations-ccollationinfo.md)|[CCollationInfo](../../data/oledb/ccollations-ccollationinfo.md)|  
|[COLUMN_PRIVILEGES](https://msdn.microsoft.com/en-us/library/ms715800.aspx)|[CColumnPrivileges](../../data/oledb/ccolumnprivileges-ccolumnprivilegeinfo.md)|[CColumnPrivilegeInfo](../../data/oledb/ccolumnprivileges-ccolumnprivilegeinfo.md)|  
|[SLOUPCE](https://msdn.microsoft.com/en-us/library/ms723052.aspx)|[CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md)|[CColumnsInfo](../../data/oledb/ccolumns-ccolumnsinfo.md)|  
|[CONSTRAINT_COLUMN_USAGE](https://msdn.microsoft.com/en-us/library/ms724522.aspx)|[CConstraintColumnUsage](../../data/oledb/cconstraintcolumnusage-cconstraintcolumnusageinfo.md)|[CConstraintColumnUsageInfo](../../data/oledb/cconstraintcolumnusage-cconstraintcolumnusageinfo.md)|  
|[CONSTRAINT_TABLE_USAGE](https://msdn.microsoft.com/en-us/library/ms713710.aspx)|[CConstraintTableUsage](../../data/oledb/cconstrainttableusage-cconstrainttableusageinfo.md)|[CConstraintTableUsageInfo](../../data/oledb/cconstrainttableusage-cconstrainttableusageinfo.md)|  
|[CHECK_CONSTRAINTS](https://msdn.microsoft.com/en-us/library/ms712845.aspx)|[CCheckConstraints](../../data/oledb/ccheckconstraints-ccheckconstraintinfo.md)|[CCheckConstraintInfo](../../data/oledb/ccheckconstraints-ccheckconstraintinfo.md)|  
|[COLUMN_DOMAIN_USAGE](https://msdn.microsoft.com/en-us/library/ms711240.aspx)|[CColumnDomainUsage](../../data/oledb/ccolumndomainusage-ccolumndomainusageinfo.md)|[CColumnDomainUsageInfo](../../data/oledb/ccolumndomainusage-ccolumndomainusageinfo.md)|  
|[FOREIGN_KEYS](https://msdn.microsoft.com/en-us/library/ms711276.aspx)|[CForeignKeys](../../data/oledb/cforeignkeys-cforeignkeysinfo.md)|[CForeignKeysInfo](../../data/oledb/cforeignkeys-cforeignkeysinfo.md)|  
|[INDEXY](https://msdn.microsoft.com/en-us/library/ms709712.aspx)|[CIndexes](../../data/oledb/cindexes-cindexinfo.md)|[CIndexInfo](../../data/oledb/cindexes-cindexinfo.md)|  
|[KEY_COLUMN_USAGE](https://msdn.microsoft.com/en-us/library/ms712990.aspx)|[CKeyColumnUsage](../../data/oledb/ckeycolumns-ckeycolumninfo.md)|[CKeyColumnUsageInfo](../../data/oledb/ckeycolumns-ckeycolumninfo.md)|  
|[PRIMARY_KEYS](https://msdn.microsoft.com/en-us/library/ms714362.aspx)|[CPrimaryKeys](../../data/oledb/cprimarykeys-cprimarykeyinfo.md)|[CPrimaryKeyInfo](../../data/oledb/cprimarykeys-cprimarykeyinfo.md)|  
|[POSTUPY](https://msdn.microsoft.com/en-us/library/ms724021.aspx)|[CProcedures](../../data/oledb/cprocedures-cprocedureinfo.md)|[CProcedureInfo](../../data/oledb/cprocedures-cprocedureinfo.md)|  
|[PROCEDURE_COLUMNS](https://msdn.microsoft.com/en-us/library/ms723092.aspx)|[CProcedureColumns](../../data/oledb/cprocedurecolumns-cprocedurecolumninfo.md)|[CProcedureColumnInfo](../../data/oledb/cprocedurecolumns-cprocedurecolumninfo.md)|  
|[PROCEDURE_PARAMETERS](https://msdn.microsoft.com/en-us/library/ms713623.aspx)|[CProcedureParameters](../../data/oledb/cprocedureparameters-cprocedureparaminfo.md)|[CProcedureParameterInfo](../../data/oledb/cprocedureparameters-cprocedureparaminfo.md)|  
|[PROVIDER_TYPES](https://msdn.microsoft.com/en-us/library/ms709785.aspx)|[CProviderTypes](../../data/oledb/cprovidertypes-cproviderinfo.md)|[CProviderInfo](../../data/oledb/cprovidertypes-cproviderinfo.md)|  
|[REFERENTIAL_CONSTRAINTS](https://msdn.microsoft.com/en-us/library/ms719737.aspx)|[CReferentialConstraints](../../data/oledb/creferentialconstraints-creferentialconstraintinfo.md)|[CReferentialConstraintInfo](../../data/oledb/creferentialconstraints-creferentialconstraintinfo.md)|  
|[SCHÉMATA](https://msdn.microsoft.com/en-us/library/ms716887.aspx)|[CSchemata](../../data/oledb/cschemata-cschematainfo.md)|[CSchemataInfo](../../data/oledb/cschemata-cschematainfo.md)|  
|[SQL_LANGUAGES](https://msdn.microsoft.com/en-us/library/ms714374.aspx)|[CSQLLanguages](../../data/oledb/csqllanguages-csqllanguageinfo.md)|[CSQLLanguageInfo](../../data/oledb/csqllanguages-csqllanguageinfo.md)|  
|[STATISTIKY](https://msdn.microsoft.com/en-us/library/ms715957.aspx)|[CStatistics](../../data/oledb/cstatistics-cstatisticinfo.md)|[CStatisticInfo](../../data/oledb/cstatistics-cstatisticinfo.md)|  
|[TABLE_CONSTRAINTS](https://msdn.microsoft.com/en-us/library/ms715921.aspx)|[CTableConstraints](../../data/oledb/ctableconstraints-ctableconstraintinfo.md)|[CTableConstraintInfo](../../data/oledb/ctableconstraints-ctableconstraintinfo.md)|  
|[TABULKY](https://msdn.microsoft.com/en-us/library/ms716980.aspx)|[CTables](../../data/oledb/ctables-ctableinfo.md)|[CTableInfo](../../data/oledb/ctables-ctableinfo.md)|  
|[TABLE_PRIVILEGES](https://msdn.microsoft.com/en-us/library/ms725428.aspx)|[CTablePrivileges](../../data/oledb/ctableprivileges-ctableprivilegeinfo.md)|[CTablePrivilegeInfo](../../data/oledb/ctableprivileges-ctableprivilegeinfo.md)|  
|[PŘEVODY](https://msdn.microsoft.com/en-us/library/ms725365.aspx)|[CTranslations](../../data/oledb/ctranslations-ctranslationinfo.md)|[CTranslationInfo](../../data/oledb/ctranslations-ctranslationinfo.md)|  
|[USAGE_PRIVILEGES](https://msdn.microsoft.com/en-us/library/ms722743.aspx)|[CUsagePrivileges](../../data/oledb/cusageprivileges-cusageprivilegeinfo.md)|[CUsagePrivilegeInfo](../../data/oledb/cusageprivileges-cusageprivilegeinfo.md)|  
|[VIEW_COLUMN_USAGE](https://msdn.microsoft.com/en-us/library/ms714896.aspx)|[CViewColumnUsage](../../data/oledb/cviewcolumnusage-cviewcolumninfo.md)|[CViewColumnInfo](../../data/oledb/cviewcolumnusage-cviewcolumninfo.md)|  
|[ZOBRAZENÍ](https://msdn.microsoft.com/en-us/library/ms723122.aspx)|[CViews](../../data/oledb/cviews-cviewinfo.md)|[CViewInfo](../../data/oledb/cviews-cviewinfo.md)|  
|[VIEW_TABLE_USAGE](https://msdn.microsoft.com/en-us/library/ms719727.aspx)|[CViewTableUsage](../../data/oledb/cviewtableusage-cviewtableinfo.md)|[CViewTableInfo](../../data/oledb/cviewtableusage-cviewtableinfo.md)|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldbsch.h  
  
## <a name="see-also"></a>Viz také  
 [CRestrictions – třída](../../data/oledb/crestrictions-class.md)