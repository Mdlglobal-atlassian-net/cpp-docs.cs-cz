---
title: "BEGIN_ACCESSOR_MAP – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BEGIN_ACCESSOR_MAP
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_ACCESSOR_MAP macro
ms.assetid: e6d6e3a4-62fa-4e49-8c53-caf8c9d20091
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b12932cb65adda391944cab5a8a4df053e2c9be4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="beginaccessormap"></a>BEGIN_ACCESSOR_MAP
Označuje začátek položek mapování přistupujícího objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BEGIN_ACCESSOR_MAP(x, num)  
```  
  
#### <a name="parameters"></a>Parametry  
 *x*  
 [v] Název třídy záznamu uživatele.  
  
 Poče  
 [v] Počet přístupových objektů v této mapě přistupujícího objektu.  
  
## <a name="remarks"></a>Poznámky  
 V případě více přístupových objektů pro sadu řádků, je třeba zadat `BEGIN_ACCESSOR_MAP` na začátku a použití `BEGIN_ACCESSOR` makro pro každé jednotlivé přistupujícího objektu. `BEGIN_ACCESSOR` Makro byla dokončena s `END_ACCESSOR` makro. Přistupující objekt mapy byla dokončena s `END_ACCESSOR_MAP` makro.  
  
 Pokud máte pouze jeden přistupujícího objektu v záznamu uživatele, použijte makro [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).  
  
## <a name="example"></a>Příklad  

 ```cpp  
class CArtistsAccessor
{
public:
// Data Elements
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];
   short m_nAge;

// Output binding map
BEGIN_ACCESSOR_MAP(CArtistsAccessor, 2)
   BEGIN_ACCESSOR(0, true)
      COLUMN_ENTRY(1, m_szFirstName)
      COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false) // Not an auto accessor
      COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsAccessor, L" \
   SELECT \
      FirstName, \
      LastName, \
      Age \
      FROM Artists")
};
 ```

  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)