---
title: CCommand::Open | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
dev_langs: C++
helpviewer_keywords: Open method
ms.assetid: 4c9b8f31-faf3-452d-9a29-3d3e5f54d6f8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 13945181ac92ec35e0b252f31382202414333bc6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccommandopen"></a>CCommand::Open
Spustí a volitelně váže příkaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT Open(  
   const CSession& session,  
   LPCWSTR wszCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
HRESULT Open(  
   const CSession& session,  
   LPCSTR szCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
HRESULT Open(  
   const CSession& session,  
   INT szCommand = NULL,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
HRESULT Open(  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `session`  
 [v] Relace, ve kterém se má spustit příkaz.  
  
 `wszCommand`  
 [v] Provedení příkazu, předat jako řetězec znaků Unicode. Může být **NULL** při použití `CAccessor`, v takovém případě bude příkaz načten z hodnoty předaný [DEFINE_COMMAND](../../data/oledb/define-command.md) makro. V tématu [ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) v *referenční příručka programátora technologie OLE DB* podrobnosti.  
  
 `szCommand`  
 [v] Stejné jako `wszCommand` s tím rozdílem, že tento parametr má příkaz řetězce ANSI. Čtvrtý formu tato metoda může trvat hodnotu NULL. Později v tomto tématu podrobnosti najdete v části "Poznámky".  
  
 *pPropSet*  
 [v] Ukazatel na pole [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury obsahující vlastnosti a hodnoty nastavení. V tématu [sady vlastností a vlastnost skupiny](https://msdn.microsoft.com/en-us/library/ms713696.aspx) v *referenční příručka programátora prostředí OLE DB* ve Windows SDK.  
  
 `pRowsAffected`  
 [vstup/výstup] Ukazatel na paměti, kde je vrácen počet ovlivněných příkazem řádků. Pokud  *\*pRowsAffected* je **NULL**, je vrácen žádný počet řádků. V opačném **otevřete** nastaví *`pRowsAffected` za následujících podmínek:  
  
|If|Pak...|  
|--------|----------|  
|**CParamSets** element `pParams` je větší než 1.|*`pRowsAffected`představuje celkový počet řádků, vliv na všechny zadané v provádění sady parametrů.|  
|Počet ovlivněných řádků není k dispozici|*`pRowsAffected`je nastavena na hodnotu -1.|  
|Příkaz neprovede aktualizaci, odstranění nebo vložení řádků|*`pRowsAffected`není definován.|  
  
 `guidCommand`  
 [v] Identifikátor GUID, který určuje syntaxi a obecná pravidla pro zprostředkovatele, který má používat při analýze text příkazu. V tématu [ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) a [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709757.aspx) v *referenční příručka programátora technologie OLE DB* podrobnosti.  
  
 `bBind`  
 [v] Určuje, jestli se vytvořit vazbu příkaz automaticky po spouštěna. Výchozí hodnota je **true**, což způsobí, že příkaz, který má být vázána automaticky. Nastavení `bBind` k **false** brání automatické vazby příkaz tak, aby můžete ručně vytvořit vazbu. (Ruční vazba je zajímají hlavně o uživatelům OLAP).  
  
 `ulPropSets`  
 [v] Počet [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury předaná *pPropSet* argument.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 První tři formy **otevřete** trvat relaci, vytvoření příkazu a spustit příkaz vazby žádné parametry podle potřeby.  
  
 První formu **otevřete** trvá příkazového řetězce Unicode a nemá žádnou výchozí hodnotu.  
  
 O druhou podobu **otevřete** přebírá řetězec příkaz ANSI a neexistuje žádná výchozí hodnota (kvůli zpětné kompatibilitě se stávajícími aplikacemi ANSI).  
  
 Třetí formu **otevřete** umožňuje příkaz řetězec, který má být NULL, z důvodu typu `int` výchozí hodnotu Null. Je poskytována pro volání `Open(session, NULL);` nebo `Open(session);` protože NULL je typu `int`. Tato verze vyžaduje a vyhodnotí, který `int` parametr mít hodnotu NULL.  
  
 Čtvrtý tvar **otevřete** Pokud jste již vytvořili příkaz a chcete provést jeden [Příprava](../../data/oledb/ccommand-prepare.md) a více spuštěních.  
  
> [!NOTE]
>  **Otevřete** volání **Execute**, který volá `GetNextResult`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CCommand – třída](../../data/oledb/ccommand-class.md)