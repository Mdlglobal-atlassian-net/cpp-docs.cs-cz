---
title: Třída CDaoFieldExchange | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
dev_langs:
- C++
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b4f702f619eb06a11cbbf7ec5be7407d12f7f445
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368726"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange – třída
Podporuje rutiny výměna pole záznamu exchange (DFX) používá databázové třídy DAO.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDaoFieldExchange  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|Vrátí nenulové hodnoty, pokud aktuální operace je vhodné pro typ pole aktualizované.|  
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|Určuje typ člena data sady záznamů – sloupec nebo parametr – reprezentována všechny následné volání funkcí DFX až další volání `SetFieldType`.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoFieldExchange::m_nOperation](#m_noperation)|DFX operaci prováděného aktuální volání sady záznamů `DoFieldExchange` – členská funkce.|  
|[CDaoFieldExchange::m_prs](#m_prs)|Ukazatel na sadu záznamů, do které DFX se provádí operace.|  
  
## <a name="remarks"></a>Poznámky  
 `CDaoFieldExchange` nemá základní třídu.  
  
 Tuto třídu použít, pokud píšete rutiny výměny dat pro vlastní datové typy; jinak nebudete používat přímo tuto třídu. DFX výměny dat mezi pole datových členů z vaší [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt a odpovídající pole ve zdroji dat na aktuální záznam. DFX spravuje exchange v obou směrech ze zdroje dat a ke zdroji dat. V tématu [Technická poznámka 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) informace o vytváření vlastní rutiny DFX.  
  
> [!NOTE]
>  Databázové třídy DAO se liší od třídami databází MFC založené na připojení ODBC (Open Database). Všechny názvy tříd DAO databáze mít předponu "CDao". Můžete i nadále přístup ke zdrojům dat ODBC s třídy DAO. Obecně platí třídy MFC založené na rozhraní DAO schopné více než třídy MFC založené na rozhraní ODBC. Třídy založené na rozhraní DAO přístup k datům, včetně prostřednictvím ovladače ODBC prostřednictvím svých vlastních databázového stroje. Také podporují jazyka DDL (Data Definition) operace, jako je například přidávání tabulek prostřednictvím třídy místo nutnosti volání rozhraní DAO sami.  
  
> [!NOTE]
>  Výměna pole záznamu rozhraní DAO (DFX) je velmi podobný výměna pole záznamu (RFX) v databázové třídy MFC založených na rozhraní ODBC ( `CDatabase`, `CRecordset`). Pokud budete rozumět tomu RFX, zjistíte, je snadno použitelný DFX.  
  
 A `CDaoFieldExchange` objekt poskytuje kontextové informace potřebné pro rozhraní DAO záznam pole exchange proběhla. `CDaoFieldExchange` objekty podporují několik operací, včetně vázané parametry a pole datových členů a nastavení různé příznaky na pole na aktuální záznam. DFX operací na členy třídy sady záznamů dat typy definované `enum` **typ pole** v `CDaoFieldExchange`. Možné **typ pole** hodnoty jsou:  
  
- **CDaoFieldExchange::outputColumn** pro pole datových členů.  
  
- **CDaoFieldExchange::param** pro parametry datových členů.  
  
 [IsValidOperation](#isvalidoperation) členské funkce je k dispozici pro psaní vlastního vlastní rutiny DFX. Budete používat [SetFieldType](#setfieldtype) často ve vaší [CDaoRecordset::DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) funkce. Podrobnosti o globální funkce DFX najdete v tématu [funkce výměny polí v záznamu](../../mfc/reference/record-field-exchange-functions.md). Informace o vytváření vlastní rutiny DFX pro vlastní datové typy najdete v tématu [Technická poznámka 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CDaoFieldExchange`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
##  <a name="isvalidoperation"></a>  CDaoFieldExchange::IsValidOperation  
 Pokud píšete DFX funkce, zavolejte `IsValidOperation` na začátku funkce k určení, zda aktuální operaci lze provést na konkrétní typ člena dat ( **CDaoFieldExchange::outputColumn** nebo **CDaoFieldExchange::param**).  
  
```  
BOOL IsValidOperation();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud aktuální operace je vhodný pro typ pole aktualizované.  
  
### <a name="remarks"></a>Poznámky  
 Některé operace, provádí mechanismus DFX platí pouze pro jeden z typů možné pole. Postupujte podle modelu stávající funkce DFX.  
  
 Další informace o psaní vlastní rutiny DFX najdete v tématu [Technická poznámka 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).  
  
##  <a name="m_noperation"></a>  CDaoFieldExchange::m_nOperation  
 Určuje operaci provést na [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt přidružený k objektu exchange pole.  
  
### <a name="remarks"></a>Poznámky  
 `CDaoFieldExchange` Objekt poskytuje kontext pro několik různých operací DFX v sadě záznamů.  
  
> [!NOTE]
>  **PSEUDONULL** hodnota popsané v části MarkForAddNew a SetFieldNull operace níže je hodnotou používá se k označení pole hodnotu Null. Mechanismus výměny výměna pole záznamu (DFX) používá tato hodnota k určení pole, která byla explicitně označena hodnotu Null. **PSEUDONULL** nevyžaduje [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) a [COleCurrency](../../mfc/reference/colecurrency-class.md) pole.  
  
 Možné hodnoty **m_nOperation** jsou:  
  
|Operace|Popis|  
|---------------|-----------------|  
|**AddToParameterList**|Sestavení **parametry** klauzule příkaz jazyka SQL.|  
|**AddToSelectList**|Sestavení **vyberte** klauzule příkaz jazyka SQL.|  
|**BindField**|Pole v databázi se váže k umístění v paměti v aplikaci.|  
|**BindParam**|Nastaví hodnoty parametrů pro dotaz sady záznamů.|  
|**Oprava**|Nastaví stav pole hodnotu Null.|  
|**AllocCache**|Přiděluje mezipaměti ke kontrole "nekonzistence" pole v sadě záznamů.|  
|**StoreField**|Uloží do mezipaměti na aktuální záznam.|  
|**LoadField**|Obnoví data uložená v mezipaměti členským proměnným v sadě záznamů.|  
|**FreeCache**|Uvolní mezipaměti ke kontrole "nekonzistence" pole v sadě záznamů.|  
|`SetFieldNull`|Nastaví stav tohoto pole na hodnotu Null a hodnota, která má **PSEUDONULL**.|  
|**MarkForAddNew**|Označí pole "nekonzistence", pokud není **PSEUDONULL**.|  
|**MarkForEdit**|Označí pole "nekonzistence" Pokud se neshodují mezipaměti.|  
|**SetDirtyField**|Nastaví pole hodnoty, které jsou označené jako "chybná."|  
|**DumpField**|Vypíše obsah pole (pouze ladění).|  
|**MaxDFXOperation**|Použít pro kontrolu vstupní.|  
  
##  <a name="m_prs"></a>  CDaoFieldExchange::m_prs  
 Obsahuje odkazy [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt přidružený k `CDaoFieldExchange` objektu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setfieldtype"></a>  CDaoFieldExchange::SetFieldType  
 Volání `SetFieldType` ve vaší `CDaoRecordset` třídy `DoFieldExchange` přepsat.  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>Parametry  
 `nFieldType`  
 Hodnota **výčtu typ pole**, deklarované v `CDaoFieldExchange`, může být buď z následujících akcí:  
  
- **CDaoFieldExchange::outputColumn**  
  
- **CDaoFieldExchange::param**  
  
### <a name="remarks"></a>Poznámky  
 Za normálních okolností ClassWizard zapíše toto volání za vás. Pokud napíšete vlastní funkce a použili průvodce k vytvoření vašeho `DoFieldExchange` fungovat, přidejte volání vlastní funkce mimo pole mapy. Pokud použijete průvodce, nebudete se mapování polí. Volání předchází volání funkcí DFX, jeden pro každé pole datového člena třídy a typ pole jako **CDaoFieldExchange::outputColumn**.  
  
 Pokud jste Parametrizace vaší třídy sady záznamů, můžete přidat DFX volání pro všechny parametry datových členů (mimo mapování polí) a předcházet těchto volání pomocí volání `SetFieldType`. Předejte hodnotu **CDaoFieldExchange::param**. (Místo toho můžete použít [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) a nastavení jeho hodnoty parametru.)  
  
 Obecně platí, každou skupinu volání funkce DFX přidružené pole datových členů nebo parametry datových členů musí předcházet volání `SetFieldType`. `nFieldType` Parametr jednotlivých `SetFieldType` volání jsou uvedeny typy datových členů reprezentována DFX volání funkce, které následují `SetFieldType` volání.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)
