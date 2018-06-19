---
title: Cdaoindexinfo – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoIndexInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Indexes collection
- CDaoIndexInfo structure [MFC]
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d8c98181a9ec049308d7b85e57c028740927cc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367032"
---
# <a name="cdaoindexinfo-structure"></a>CDaoIndexInfo – struktura
`CDaoIndexInfo` Struktura obsahuje informace o objektu indexu definované pro přístup k objektům dat (DAO).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoIndexInfo {  
    CDaoIndexInfo();
*// Constructor  
    CString m_strName;  // Primary  
    CDaoIndexFieldInfo* m_pFieldInfos;  // Primary  
    short m_nFields;    // Primary  
    BOOL m_bPrimary;    // Secondary  
    BOOL m_bUnique;     // Secondary  
    BOOL m_bClustered;  // Secondary  
    BOOL m_bIgnoreNulls;                // Secondary  
    BOOL m_bRequired;   // Secondary  
    BOOL m_bForeign;    // Secondary  
    long m_lDistinctCount;              // All  
 *// Below the // Implementation comment: *// Destructor, not otherwise documented  
};   
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Objekt pole jedinečné názvy. Podrobnosti naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO.  
  
 `m_pFieldInfos`  
 Ukazatel na pole [cdaoindexfieldinfo –](../../mfc/reference/cdaoindexfieldinfo-structure.md) objekty o tom, která tabledef nebo sada záznamů pole klíčová pole v indexu. Každý objekt identifikuje jedno pole v indexu. Výchozí index řazení je vzestupně. Index objekt může mít jedno či více polí představující index klíče pro každý záznam. To může být vzestupné, sestupně, nebo jejich kombinaci.  
  
 `m_nFields`  
 Počet polí, které jsou uložené v `m_pFieldInfos`.  
  
 *m_bPrimary*  
 Pokud je vlastnost primární **TRUE**, objekt index představuje primární index. Primární index se skládá z jednoho nebo více polí, které jedinečně identifikují všechny záznamy v tabulce v předdefinovaném pořadí. Protože index pole musí být jedinečný, jedinečný Index objektu je také nastavena na **TRUE** v rozhraní DAO. Pokud primární index se skládá z více než jedno pole, každé pole může obsahovat duplicitní hodnoty, ale kombinace hodnot z indexovaného pole musí být jedinečný. Primární index se skládá z klíče pro tabulku a obvykle obsahuje pole stejný jako primární klíč.  
  
 Když nastavíte primární klíč pro tabulku, primární klíč je automaticky definovaný jako primární index pro tabulku. Další informace najdete v tématech "Primární vlastnost" a "Jedinečnou vlastnost" v nápovědě rozhraní DAO.  
  
> [!NOTE]
>  Může být, maximálně jeden primární index v tabulce.  
  
 *m_bUnique*  
 Určuje, zda objekt index představuje jedinečný index pro tabulku. Pokud je tato vlastnost **TRUE**, objekt index představuje index, který je jedinečný. Jedinečný index se skládá z jednoho nebo více polí, které logicky uspořádat všechny záznamy v tabulce v pořadí od jedinečný, předdefinované. Pokud index se skládá z jednoho pole, hodnoty v tomto poli musí být jedinečné pro celou tabulku. Pokud je index tvořen více než jedno pole, každé pole může obsahovat duplicitní hodnoty, ale kombinace hodnot z indexovaného pole musí být jedinečný.  
  
 Pokud mají vlastnosti jedinečný i primární index objektu **TRUE**, index je jedinečný a primární: Toto číslo jednoznačně identifikuje všechny záznamy v tabulce v předdefinované a logickém pořadí. Pokud je primární vlastnost nastavena **FALSE**, index je sekundární index. Sekundární indexy (klíče i nonkey) logicky uspořádat záznamy v předdefinovaném pořadí bez slouží jako identifikátor pro záznamy v tabulce.  
  
 Další informace najdete v tématech "Primární vlastnost" a "Jedinečnou vlastnost" v nápovědě rozhraní DAO.  
  
 *m_bClustered*  
 Určuje, zda objekt index představuje clusterovaný index pro tabulku. Pokud je tato vlastnost **TRUE**, objekt index představuje clusterovaný index; jinak, je nepoužívá. Clusterovaný index se skládá z jednoho nebo více nonkey polí, která, dohromady, uspořádat všechny záznamy v tabulce v předdefinovaném pořadí. Clusterovaný index data v tabulce oznámena uložena v pořadí zadaném clusterovaný index. Clusterovaný index poskytuje efektivní přístup k záznamům v tabulce. Další informace naleznete v tématu "Clusterovaný vlastnost" v nápovědě rozhraní DAO.  
  
> [!NOTE]
>  U databází, které používají databázový stroj Microsoft Jet, protože tento databázový stroj nepodporuje Clusterované indexy se ignoruje vlastnost clusteru.  
  
 *m_bIgnoreNulls*  
 Určuje, zda jsou index položky záznamů, které mají hodnoty Null v jejich index pole. Pokud je tato vlastnost **TRUE**, pole s hodnotami Null nemají položka indexu. Chcete-li vyhledat záznamů pomocí pole rychlejší, můžete definovat index pole. Je-li povolit položky Null v indexovaného pole a očekávají, že mnoho položek na hodnotu Null, můžete nastavit vlastnost pro daný objekt index do **TRUE** ke snížení objemu prostoru úložiště, který používá index. Nastavení vlastnosti Ignorovat hodnoty Null a nastavení požadovaná vlastnost společně určit, zda záznam s hodnotou Null indexu má položka, jak ukazuje následující tabulka.  
  
|Ignorovat hodnoty Null|Požadováno|Index pole hodnotu Null|  
|-----------------|--------------|-------------------------|  
|Hodnota TRUE|False|Hodnota Null povoleny; nebyla přidána žádná položka index.|  
|False|False|Hodnota Null povoleny; přidala se položka indexu.|  
|True nebo False|Hodnota TRUE|Hodnota Null není povoleno; nebyla přidána žádná položka index.|  
  
 Další informace naleznete v tématu "Vlastnost" v nápovědě rozhraní DAO.  
  
 `m_bRequired`  
 Určuje, zda objekt DAO index vyžaduje nenulovou hodnotu. Pokud je tato vlastnost **TRUE**, objekt index nepovoluje hodnotu Null. Další informace naleznete v tématu "Požadované vlastnosti" v nápovědě rozhraní DAO.  
  
> [!TIP]
>  Když nastavíte tuto vlastnost pro objekt DAO index nebo objekt pole (obsažený v tabledef, sada záznamů nebo querydef objektu), nastavit pro objekt pole. Před u objektu indexu se kontroluje platnost nastavení vlastností pro objekt pole.  
  
 *m_bForeign*  
 Určuje, zda objekt index představuje cizí klíč v tabulce. Pokud je tato vlastnost **TRUE**, index představuje cizí klíč v tabulce. Cizí klíč, který se skládá z jedné nebo více polí v cizí tabulce, které jedinečně identifikují řádek v primární tabulce. Databázový stroj Microsoft Jet vytvoří objekt indexu pro tabulku cizí a nastaví vlastnost cizí, když vytvoříte vztah, který vynucuje referenční integrity. Další informace naleznete v tématu "Cizí vlastnost" v nápovědě rozhraní DAO.  
  
 *m_lDistinctCount*  
 Označuje počet jedinečné hodnoty pro objekt indexu, které jsou zahrnuty v tabulce přidružené. Zkontrolujte vlastnost DistinctCount můžete určit počet jedinečných hodnot nebo klíče v indexu. Všechny klíče se počítá jenom jednou, i když může mít vícenásobné výskyty této hodnotě index umožňuje duplicitní hodnoty. Tyto informace jsou užitečné v aplikacích, které se pokoušejí o optimalizaci přístupu k datům vyhodnocením index informace. Počet jedinečných hodnot se taky říká Kardinalita objektu indexu. Vlastnost DistinctCount nebude vždy odráží skutečný počet klíčů v určitou dobu. Například změnu způsobené odvolání transakce se neprojeví okamžitě ve vlastnosti DistinctCount. Další informace naleznete v tématu "DistinctCount vlastnost" v nápovědě rozhraní DAO.  
  
## <a name="remarks"></a>Poznámky  
 Odkazy na primární, sekundární a všechny výše označuje, jak je vrácené informace `GetIndexInfo` členské funkce ve třídách [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) a [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).  
  
 Index objekty nejsou reprezentované pomocí třídy knihovny MFC. Místo toho rozhraní DAO objekty základní MFC objekty třídy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obsahovat kolekce objektů index názvem kolekce indexů. Členské funkce pro přístup k jednotlivé položky index informace zadat tyto třídy nebo jejich najednou pomocí `CDaoIndexInfo` objekt voláním `GetIndexInfo` členské funkce obsahující objektu.  
  
 `CDaoIndexInfo` má konstruktor a destruktor, aby bylo možné správně přidělit a navrátit informace index pole v `m_pFieldInfos`.  
  
 Načte informace `GetIndexInfo` členské funkce tabledef objektu je uložen v `CDaoIndexInfo` struktura. Volání `GetIndexInfo` členské funkce obsahující tabledef objektu, v jehož kolekce indexů index objekt se uloží. `CDaoIndexInfo` také definuje `Dump` – členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoIndexInfo` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)

