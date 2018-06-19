---
title: Uživatelské záznamy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_MAP
dev_langs:
- C++
helpviewer_keywords:
- rowsets [C++], accessors
- COLUMN_ENTRY macro
- COLUMN_ENTRY_MAP macro
- user records, OLE DB consumer templates
- OLE DB consumer templates, user records
- CAccessor class, example
- BEGIN_ACCESSOR_MAP macro
- accessors [C++], rowsets
- accessors [C++], static
- BEGIN_ACCESSOR macro, example
ms.assetid: 2de9e5eb-53ce-42b1-80fa-57d46600a80c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aea6b4b2ebb1a02e4ef669b437fbe7eb30937f9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33109804"
---
# <a name="user-records"></a>Uživatelské záznamy
Použití statické přístupového objektu (tedy přistupující objekt odvozený z **CAccessor)**, váš příjemce musí mít uživatelský záznam. Záznamu uživatele je C++ třídu, která obsahuje elementy data pro zpracování vstupu nebo výstupu. Průvodce příjemcem knihovny ATL technologie OLE DB generuje záznamu uživatele pro vaše příjemce. Metody můžete přidat do uživatelského záznamu pro volitelné úkoly, jako je zpracování příkazů.  
  
 Následující kód ukazuje záznam ukázka, která zpracovává příkazy. V záznamu uživatele `BEGIN_COLUMN_MAP` představuje sadu řádků dat předaný příjemce od zprostředkovatele. `BEGIN_PARAM_MAP` představuje sadu parametrů příkazu. Tento příklad používá [CCommand](../../data/oledb/ccommand-class.md) třídy pro zpracování parametrů příkazu. Datové členy v položek mapování představují posun do jednoho souvislého bloku paměti pro každou instanci třídy. `COLUMN_ENTRY` Makra odpovídají `PROVIDER_COLUMN_ENTRY` makra na straně zprostředkovatele.  
  
 Další informace o **COLUMN_MAP** a **PARAM_MAP** makra, najdete v části [makra pro šablony příjemce technologie OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
```  
class CArtists  
{  
public:  
// Data Elements  
   CHAR m_szFirstName[20];  
   CHAR m_szLastName[30];  
   short m_nAge;  
  
// Column binding map  
BEGIN_COLUMN_MAP(CArtists)  
   COLUMN_ENTRY(1, m_szFirstName)  
   COLUMN_ENTRY(2, m_szLastName)  
   COLUMN_ENTRY(3, m_nAge)  
END_COLUMN_MAP()  
  
// Parameter binding map  
BEGIN_PARAM_MAP(CArtists)  
   COLUMN_ENTRY(1, m_nAge)  
END_PARAM_MAP()  
};  
```  
  
## <a name="wizard-generated-user-records"></a>Generované průvodcem uživatelské záznamy  
 Pokud používáte průvodce příjemcem knihovny ATL technologie OLE DB pro vygenerování příjemce, máte možnost použití šablony technologie OLE DB nebo OLE DB atributy. Generovaný kód se liší v každém případu. Další informace o tomto kódu najdete v tématu [vygenerované třídy](../../data/oledb/consumer-wizard-generated-classes.md).  
  
## <a name="user-record-support-for-multiple-accessors"></a>Podpora uživatelského záznamu pro několik přístupových objektů  
 Podrobné informace o scénářích, ve kterých budete muset použít několik přístupových objektů, najdete v části [použití více přístupových objektů pro sadu řádků](../../data/oledb/using-multiple-accessors-on-a-rowset.md).  
  
 Následující příklad ukazuje uživatelský záznam upravit tak, aby podporují několik přístupových objektů na sadě řádků. Místo `BEGIN_COLUMN_MAP` a `END_COLUMN_MAP`, používá [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md) a [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) pro každý přistupující objekt. `BEGIN_ACCESSOR` Makro Určuje číslo přistupujícího objektu (posun od nuly) a zda je přistupující objekt automaticky přistupující objekt. Volání načtel `GetData` k načtení dat automaticky na volání [MoveNext](../../data/oledb/crowset-movenext.md). Manuální přístupové objekty vyžadují, abyste explicitně načíst data. Manuální přistupující objekt použijte, pokud vytváříte vazbu na velkých objemů dat pole (například rastrový obrázek), které možná nebudete chtít načíst pro každý záznam.  
  
```  
class CMultiArtists  
{  
public:  
// Data Elements  
   CHAR m_szFirstName[20];  
   CHAR m_szLastName[30];  
   short m_nAge;  
  
// Column binding map  
BEGIN_ACCESSOR_MAP(CMultiArtists, 2)  
   BEGIN_ACCESSOR(0, true)    // true specifies an auto accessor  
    COLUMN_ENTRY(1, m_szFirstName)  
    COLUMN_ENTRY(2, m_szLastName)  
   END_ACCESSOR()  
   BEGIN_ACCESSOR(1, false)   // false specifies a manual accessor  
    COLUMN_ENTRY(3, m_nAge)  
   END_ACCESSOR()  
END_ACCESSOR_MAP()  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)