---
title: Cdaofieldinfo – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d08dd9d877d8872c5c8a930e84ae0496c745709
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368404"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo – struktura
`CDaoFieldInfo` Struktura obsahuje informace o objekt pole definované pro přístup k objektům dat (DAO).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoFieldInfo  
{  
    CString m_strName;           // Primary  
    short m_nType;               // Primary  
    long m_lSize;                // Primary  
    long m_lAttributes;          // Primary  
    short m_nOrdinalPosition;    // Secondary  
    BOOL m_bRequired;            // Secondary  
    BOOL m_bAllowZeroLength;     // Secondary  
    long m_lCollatingOrder;      // Secondary  
    CString m_strForeignName;    // Secondary  
    CString m_strSourceField;    // Secondary  
    CString m_strSourceTable;    // Secondary  
    CString m_strValidationRule; // All  
    CString m_strValidationText; // All  
    CString m_strDefaultValue;   // All  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Objekt pole jedinečné názvy. Podrobnosti naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO.  
  
 `m_nType`  
 Hodnota, která určuje datový typ pole. Podrobnosti naleznete v tématu "Vlastnost typu" v nápovědě rozhraní DAO. Hodnota této vlastnosti může být jeden z následujících akcí:  
  
- **dbBoolean** Ano/Ne, stejné jako **TRUE**/**FALSE**  
  
- **dbByte** bajtů  
  
- **dbInteger** krátké  
  
- **dbLong** dlouho  
  
- **dbCurrency** měna; viz třídy knihovny MFC [COleCurrency](../../mfc/reference/colecurrency-class.md)  
  
- **dbSingle** jeden  
  
- **dbDouble** Double  
  
- **dbDate** datum a čas; viz třídy knihovny MFC [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)  
  
- **dbText** Text; viz třídy knihovny MFC [CString](../../atl-mfc-shared/reference/cstringt-class.md)  
  
- **dbLongBinary** dlouhá binární (OLE Object); můžete chtít použít třídy MFC [CByteArray](../../mfc/reference/cbytearray-class.md) místo třída `CLongBinary` jako `CByteArray` je bohatší a snadněji použitelná.  
  
- **dbMemo** Memo; viz třídy knihovny MFC `CString`  
  
- **dbGUID** A globálně jedinečný identifikátor nebo univerzálně jedinečný identifikátor použít s vzdálených volání procedur. Další informace naleznete v tématu "Vlastnost typu" v nápovědě rozhraní DAO.  
  
> [!NOTE]
>  Nepoužívejte řetězce pro binární data. To způsobí, že vaše data předávat vrstvě překlad Unicode/ANSI, výsledkem je vyšší nároky a může být neočekávaná překlad.  
  
 *m_lSize*  
 Hodnota, která určuje maximální velikost v bajtech objekt DAO pole, který obsahuje text nebo pevnou velikost pole objekt, který obsahuje textové nebo číselné hodnoty. Podrobnosti naleznete v tématu "Velikost vlastnost" v nápovědě rozhraní DAO. Velikost může být jedna z následujících hodnot:  
  
|Typ|Velikost (bajty)|Popis|  
|----------|--------------------|-----------------|  
|**dbBoolean**|1 bajt|Ano (stejný jako True nebo False)|  
|**dbByte**|1|Byte|  
|**dbInteger**|2|Integer|  
|**dbLong**|4|dlouhá|  
|**dbCurrency**|8|Měna ([COleCurrency](../../mfc/reference/colecurrency-class.md))|  
|**dbSingle**|4|Single|  
|**dbDouble**|8|Double|  
|**dbDate**|8|Datum a čas ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|  
|**dbText**|1 - 255|Text ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbLongBinary**|0|Dlouhá binární (objekt OLE; [CByteArray](../../mfc/reference/cbytearray-class.md); použít místo `CLongBinary`)|  
|**dbMemo**|0|Memo ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbGUID**|16|Globálně jedinečný identifikátor nebo univerzálně jedinečný identifikátor použít s vzdálených volání procedur.|  
  
 `m_lAttributes`  
 Určuje vlastnosti objektu pole obsažené ve tabledef, sada záznamů, querydef nebo index objektu. Hodnota vrácená může být součet těchto konstanty, vytvořené pomocí C++ bitové operace OR (**&#124;**) operátor:  
  
- **dbFixedField** velikost pole vyřešen (výchozí nastavení pro číselné pole).  
  
- **dbVariableField** velikosti pole je proměnná (pouze textová pole).  
  
- **dbAutoIncrField** hodnotu pole pro nové záznamy se automaticky zvýší na jedinečný dlouhé celé číslo, kterou nelze změnit. Podporováno pouze pro Microsoft Jet databázových tabulek.  
  
- **dbUpdatableField** hodnotu pole lze změnit.  
  
- **dbDescending** pole je seřazené v sestupném (Z - A, nebo 100-0) pořadí (platí pouze pro objekt pole v kolekci polí indexu objektu; v knihovně MFC, index sami objekty jsou obsažené v objektech tabledef). Pokud vynecháte tento konstanta, pole je seřadit ve vzestupném (A - Z nebo 0 - 100) pořadí (výchozí).  
  
 Při kontrole nastavení této vlastnosti, můžete použít C++ bitové – a – operátor (**&**) k testování pro konkrétní atribut. Při nastavování několik atributů, můžete je spojit kombinací příslušné konstanty s bitové operace OR (**&#124;**) operátor. Podrobnosti naleznete v tématu "Vlastnosti Attributes" v nápovědě rozhraní DAO.  
  
 *m_nOrdinalPosition*  
 Hodnota, která určuje číselného pořadí, ve kterém chcete pole reprezentována objekt DAO pole, který se má zobrazit relativně k další pole. Můžete nastavit tuto vlastnost s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield). Podrobnosti naleznete v tématu "OrdinalPosition vlastnost" v nápovědě rozhraní DAO.  
  
 `m_bRequired`  
 Určuje, zda objekt DAO pole vyžaduje hodnotu než Null. Pokud je tato vlastnost **TRUE**, pole neumožňuje hodnotu Null. V případě potřeby je nastavený na **FALSE**, pole může obsahovat hodnoty Null, jakož i hodnoty, které splňují podmínky zadané vlastnosti nastavením Povolit nulovou délku a ověřovací pravidlo. Podrobnosti naleznete v tématu "Požadované vlastnosti" v nápovědě rozhraní DAO. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 *m_bAllowZeroLength*  
 Určuje, zda prázdný řetězec ("") je platná hodnota objekt DAO pole s datovým typem Text nebo Memo. Pokud je tato vlastnost **TRUE**, prázdný řetězec je platnou hodnotu. Tuto vlastnost lze nastavit **FALSE** zajistit prázdný řetězec nelze použít k nastavení hodnoty pole. Podrobnosti naleznete v tématu "Povolit nulovou délku vlastnost" v nápovědě rozhraní DAO. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 `m_lCollatingOrder`  
 Určuje pořadí řazení v textu pro porovnání řetězců nebo řazení. Podrobnosti naleznete v tématu "Přizpůsobení Windows registru nastavení pro Data Access" v nápovědě rozhraní DAO. Seznam možných hodnot vrácených najdete v tématu **m_lCollatingOrder** členem [cdaodatabaseinfo –](../../mfc/reference/cdaodatabaseinfo-structure.md) struktura. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 `m_strForeignName`  
 Hodnota, která v vztah, určuje název pole objekt DAO v cizí tabulku, která odpovídá poli v primární tabulce. Podrobnosti naleznete v tématu "ForeignName vlastnost" v nápovědě rozhraní DAO.  
  
 *m_strSourceField*  
 Určuje název pole, která je původního zdroje dat pro objekt DAO pole obsažené ve tabledef, sada záznamů nebo querydef objektu. Tato vlastnost určuje původní název pole, které jsou přidružené k objektu pole. Například můžete tuto vlastnost použít k určení původního zdroje dat v dotazu pole, jehož název nesouvisí s název pole v podkladové tabulce. Podrobnosti naleznete v tématu "SourceField, vlastnosti SourceTable" v nápovědě rozhraní DAO. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 *m_strSourceTable*  
 Určuje název tabulky, která je původního zdroje dat pro objekt DAO pole obsažené ve tabledef, sada záznamů nebo querydef objektu. Tato vlastnost určuje původní název tabulky, který je přidružený k objektu pole. Například můžete tuto vlastnost použít k určení původního zdroje dat v dotazu pole, jehož název nesouvisí s název pole v podkladové tabulce. Podrobnosti naleznete v tématu "SourceField, vlastnosti SourceTable" v nápovědě rozhraní DAO. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 `m_strValidationRule`  
 Hodnota, která ověří data v poli, protože je změnit nebo přidat do tabulky. Podrobnosti naleznete v tématu "Vlastnosti Ověřovací pravidlo" v nápovědě rozhraní DAO. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 Související informace o tabledefs – najdete v tématu **m_strValidationRule** členem [cdaotabledefinfo –](../../mfc/reference/cdaotabledefinfo-structure.md) struktura.  
  
 `m_strValidationText`  
 Hodnota, která určuje text zprávy, která vaše aplikace zobrazí, pokud hodnota pole objekt DAO nesplňuje zadané pravidlo ověřování pomocí nastavení vlastnosti Ověřovací pravidlo. Podrobnosti naleznete v tématu "Vlastnost Ověřovací text" v nápovědě rozhraní DAO. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 *m_strDefaultValue*  
 Výchozí hodnota objekt DAO pole. Když je vytvořen nový záznam, nastavení vlastnosti výchozí hodnota se automaticky zadá, jako hodnota pro pole. Podrobnosti naleznete v tématu "Vlastnost Výchozí hodnota" v nápovědě rozhraní DAO. Můžete nastavit tuto vlastnost pro tabledef s [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
## <a name="remarks"></a>Poznámky  
 Odkazy na primární, sekundární a všechny výše označuje, jak je vrácené informace `GetFieldInfo` členské funkce ve třídách [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo), a [ CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo).  
  
 Pole objektů nejsou reprezentované pomocí třídy knihovny MFC. Místo toho základní objekty následující třídy MFC rozhraní DAO objekty obsahovat kolekce objektů pole: [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), a [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Členské funkce pro přístup k některé jednotlivých položek informací o poli zadejte tyto třídy nebo jejich najednou pomocí `CDaoFieldInfo` objekt voláním `GetFieldInfo` členské funkce obsahující objektu.  
  
 Kromě toho pro zkoumání vlastnosti objektu jeho použití, můžete také použít `CDaoFieldInfo` vytvořit vstupní parametr k vytvoření nové pole v tabledef. Jednodušší možnosti jsou k dispozici pro tento úkol, ale pokud chcete jemnějšího ovládání, můžete použít verzi [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield) , která má `CDaoFieldInfo` parametr.  
  
 Načte informace `GetFieldInfo` – členská funkce (třídy, která obsahuje pole) je uložen v `CDaoFieldInfo` struktury. Volání `GetFieldInfo` – členská funkce okrajem objektu, v jehož kolekce polí pole objekt se uloží. `CDaoFieldInfo` také definuje `Dump` – členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoFieldInfo` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)   
 [CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)   
 [CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)

