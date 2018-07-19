---
title: Agregace a makra objektu pro vytváření tříd | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_AGGREGATABLE
- atlcom/ATL::DECLARE_CLASSFACTORY
- atlcom/ATL::DECLARE_CLASSFACTORY_EX
- atlcom/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- atlcom/ATL::DECLARE_CLASSFACTORY_SINGLETON
- atlcom/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- atlcom/ATL::DECLARE_NOT_AGGREGATABLE
- atlcom/ATL::DECLARE_ONLY_AGGREGATABLE
- atlcom/ATL::DECLARE_POLY_AGGREGATABLE
- atlcom/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- atlcom/ATL::DECLARE_VIEW_STATUS
dev_langs:
- C++
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4995779a7f5595eca9dc47a29ea11d875995e959
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881224"
---
# <a name="aggregation-and-class-factory-macros"></a>Agregace a makra objektu pro vytváření tříd
Tato makra poskytují způsobů řízení agregace a deklarace objekty pro vytváření tříd.  
  
|||  
|-|-|  
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Deklaruje, že může být objekt agregovat (výchozí).|  
|[DECLARE_CLASSFACTORY](#declare_classfactory)|Deklaruje objekt pro vytváření tříd bude [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md), objekt knihovny ATL pro vytváření tříd výchozí.|  
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Deklaruje objekt factory třídy objektu pro vytváření tříd.|  
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|Deklaruje [ccomclassfactory2 –](../../atl/reference/ccomclassfactory2-class.md) bude objekt pro vytváření tříd.|  
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Deklaruje [ccomclassfactoryautothread –](../../atl/reference/ccomclassfactoryautothread-class.md) bude objekt pro vytváření tříd.|  
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Deklaruje [ccomclassfactorysingleton –](../../atl/reference/ccomclassfactorysingleton-class.md) bude objekt pro vytváření tříd.|  
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Deklaruje virtuální `GetControllingUnknown` funkce.|  
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Deklaruje, že objekt nemůže být agregován.|  
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Deklaruje, že objekt musí být agregován.|  
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Zkontroluje hodnotu vlastnosti vnější neznámá a deklaruje objekt agregovatelné nebo neagregovatelný, podle potřeby.|  
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|Chrání před odstraněním během konstrukce objektu vnitřní vnějšího objektu.|  
|[DECLARE_VIEW_STATUS](#declare_view_status)|Určuje, které příznaky do kontejneru.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
   
##  <a name="declare_aggregatable"></a>  DECLARE_AGGREGATABLE  
 Určuje, že objekt se dají agregovat.  
  
```
DECLARE_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Název třídy, kterou definujete jako agregovatelné.  
  
### <a name="remarks"></a>Poznámky  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) obsahuje tohoto makra pro určení modelu výchozí agregace. Chcete-li přepsat toto výchozí nastavení, zadejte buď [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) nebo [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) makra v definici třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]  
  
##  <a name="declare_classfactory"></a>  DECLARE_CLASSFACTORY  
 Deklaruje [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md) bude objekt pro vytváření tříd.  
  
```
DECLARE_CLASSFACTORY()
```  
  
### <a name="remarks"></a>Poznámky  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) toto makro používá k deklaraci výchozí objekt pro vytváření tříd pro objekt.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]  
  
##  <a name="ccomclassfactory_class"></a>  Ccomclassfactory – třída  
 Tato třída implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) rozhraní.  
  
```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
### <a name="remarks"></a>Poznámky  
 `CComClassFactory` implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) rozhraní, která obsahuje metody pro vytvoření objektu s konkrétní identifikátorem CLSID, jakož i uzamčení objekt pro vytváření tříd v paměti, abyste mohli rychleji vytvořit nové objekty. `IClassFactory` je nutné implementovat pro každou třídu, která zaregistrujete v systémovém registru a můžete přiřadit identifikátor CLSID.  
  
 Objekty knihovny ATL obvykle získat objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makra [DECLARE_CLASSFACTORY](#declare_classfactory), který deklaruje `CComClassFactory` jako výchozí objekt pro vytváření tříd. Chcete-li přepsat toto výchozí nastavení, zadejte jednu DECLARE_CLASSFACTORY*XXX* makra v definici třídy. Například [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) makro používá zadanou třídu pro objekt pro vytváření tříd:  
  
 [!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]  
  
 Výše uvedené definice třídy, která určuje `CMyClassFactory` se použije jako objekt pro vytváření tříd objektu výchozí. `CMyClassFactory` musí být odvozen od `CComClassFactory` a přepsat `CreateInstance`.  
  
 Knihovna ATL poskytuje tři makra, které deklarují objekt pro vytváření tříd:  
  
- [DECLARE_CLASSFACTORY2](#declare_classfactory2) používá [ccomclassfactory2 –](../../atl/reference/ccomclassfactory2-class.md), který řídí vytváření prostřednictvím licenci.  
  
- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) používá [ccomclassfactoryautothread –](../../atl/reference/ccomclassfactoryautothread-class.md), která vytváří objekty ve více objekty apartment.  
  
- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) používá [ccomclassfactorysingleton –](../../atl/reference/ccomclassfactorysingleton-class.md), což vytvoří jeden [ccomobjectglobal –](../../atl/reference/ccomobjectglobal-class.md) objektu.  
  
##  <a name="declare_classfactory_ex"></a>  DECLARE_CLASSFACTORY_EX  
 Deklaruje `cf` bude objekt pro vytváření tříd.  
  
```
DECLARE_CLASSFACTORY_EX( cf )
```  
  
### <a name="parameters"></a>Parametry  
 *CF*  
 [in] Název třídy, která implementuje třída objektu factory.  
  
### <a name="remarks"></a>Poznámky  
 *Cf* parametr musí být odvozen od [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md) a přepsat `CreateInstance` metody.  
  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) zahrnuje [DECLARE_CLASSFACTORY](#declare_classfactory) makro, které určuje `CComClassFactory` jako výchozí objekt pro vytváření tříd. Nicméně zahrnutím makra DECLARE_CLASSFACTORY_EX v definici třídy objektu přepsat toto výchozí nastavení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]  
  
##  <a name="declare_classfactory2"></a>  DECLARE_CLASSFACTORY2  
 Deklaruje [ccomclassfactory2 –](../../atl/reference/ccomclassfactory2-class.md) bude objekt pro vytváření tříd.  
  
```
DECLARE_CLASSFACTORY2( lic )
```  
  
### <a name="parameters"></a>Parametry  
 *– Licenční smlouva*  
 [in] Třídu, která implementuje `VerifyLicenseKey`, `GetLicenseKey`, a `IsLicenseValid`.  
  
### <a name="remarks"></a>Poznámky  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) zahrnuje [DECLARE_CLASSFACTORY](#declare_classfactory) makro, které určuje [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Nicméně zahrnutím makra DECLARE_CLASSFACTORY2 v definici třídy objektu přepsat toto výchozí nastavení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]  
  
##  <a name="ccomclassfactory2_class"></a>  Ccomclassfactory2 – třída  
 Tato třída implementuje [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) rozhraní.  
  
```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```    
  
### <a name="parameters"></a>Parametry  
 *Licence*  
 Třída, která implementuje následující statické funkce:  
  
- **verifylicensekey – statické BOOL (BSTR** `bstr` **);**  
  
- **getlicensekey – statické BOOL (DWORD** `dwReserved` **, BSTR\***  `pBstr` **);**  
  
- **statické BOOL IsLicenseValid ();**  
  
### <a name="remarks"></a>Poznámky  
 `CComClassFactory2` implementuje [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) rozhraní, která je rozšířením z [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364). `IClassFactory2` vytvoření ovládacích prvků objektu prostřednictvím licenci. Třída objekt pro vytváření, provádění na licencovanou počítači může poskytnout za běhu licenční klíč. Tento licenční klíč umožňuje aplikaci k vytvoření instance objektů při úplné počítač licence neexistuje.  
  
 Objekty knihovny ATL obvykle získat objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makra [DECLARE_CLASSFACTORY](#declare_classfactory), který deklaruje [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Chcete-li použít `CComClassFactory2`, zadejte [DECLARE_CLASSFACTORY2](#declare_classfactory2) makra v definici třídy objektu. Příklad:  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]  
  
 `CMyLicense`, parametr šablony `CComClassFactory2`, musí implementovat statické funkce `VerifyLicenseKey`, `GetLicenseKey`, a `IsLicenseValid`. Následuje příklad licenci jednoduše třídy:  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]  
  
 `CComClassFactory2` je odvozen z obou `CComClassFactory2Base` a *licence*. `CComClassFactory2Base`, pak je odvozena z `IClassFactory2` a **CComObjectRootEx\< CComGlobalsThreadModel >**.  
  
##  <a name="declare_classfactory_auto_thread"></a>  DECLARE_CLASSFACTORY_AUTO_THREAD  
 Deklaruje [ccomclassfactoryautothread –](../../atl/reference/ccomclassfactoryautothread-class.md) bude objekt pro vytváření tříd.  
  
```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```  
  
### <a name="remarks"></a>Poznámky  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) zahrnuje [DECLARE_CLASSFACTORY](#declare_classfactory) makro, které určuje [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Nicméně zahrnutím makra DECLARE_CLASSFACTORY_AUTO_THREAD v definici třídy objektu přepsat toto výchozí nastavení.  
  
 Při vytváření objektů v několika objekty apartment (v režimu out-of-proc serveru) přidejte DECLARE_CLASSFACTORY_AUTO_THREAD do vaší třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]  
  
##  <a name="ccomclassfactoryautothread_class"></a>  Ccomclassfactoryautothread – třída  
 Tato třída implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) rozhraní a umožňuje objektů bude vytvořena ve více objekty apartment.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
### <a name="remarks"></a>Poznámky  
 `CComClassFactoryAutoThread` je podobný [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md), ale umožňuje objektů bude vytvořena ve více objekty apartment. Využít této podpory, jsou odvozeny z modulu EXE [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
 Objekty knihovny ATL obvykle získat objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makra [DECLARE_CLASSFACTORY](#declare_classfactory), který deklaruje [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Chcete-li použít `CComClassFactoryAutoThread`, zadejte [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) makra v definici třídy objektu. Příklad:  
  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]  
  
##  <a name="declare_classfactory_singleton"></a>  DECLARE_CLASSFACTORY_SINGLETON  
 Deklaruje [ccomclassfactorysingleton –](../../atl/reference/ccomclassfactorysingleton-class.md) bude objekt pro vytváření tříd.  
  
```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```  
  
### <a name="parameters"></a>Parametry  
 *obj*  
 [in] Název třídy objektu.  
  
### <a name="remarks"></a>Poznámky  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) zahrnuje [DECLARE_CLASSFACTORY](#declare_classfactory) makro, které určuje [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Nicméně zahrnutím makra DECLARE_CLASSFACTORY_SINGLETON v definici třídy objektu přepsat toto výchozí nastavení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]  
  
##  <a name="ccomclassfactorysingleton_class"></a>  Ccomclassfactorysingleton – třída  
 Tato třída je odvozena z [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md) a používá [ccomobjectglobal –](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Třída.  
  
 `CComClassFactorySingleton` je odvozen od [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md) a používá [ccomobjectglobal –](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu. Každé volání `CreateInstance` metoda jednoduše dotazuje tohoto objektu pro ukazatel rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Objekty knihovny ATL obvykle získat objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makra [DECLARE_CLASSFACTORY](#declare_classfactory), který deklaruje `CComClassFactory` jako výchozí objekt pro vytváření tříd. Chcete-li použít `CComClassFactorySingleton`, zadejte [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) makra v definici třídy objektu. Příklad:  
  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]  
  
##  <a name="declare_get_controlling_unknown"></a>  DECLARE_GET_CONTROLLING_UNKNOWN  
 Deklaruje virtuální funkci `GetControllingUnknown`.  
  
```
DECLARE_GET_CONTROLLING_UNKNOWN()
```  
  
### <a name="remarks"></a>Poznámky  
 Přidat toto makro do objektu, pokud se zobrazí chybová zpráva kompilátoru `GetControllingUnknown` není definován (například v `CComAggregateCreator`).  
  
##  <a name="declare_not_aggregatable"></a>  DECLARE_NOT_AGGREGATABLE  
 Určuje, že objekt nemůže být agregován.  
  
```
DECLARE_NOT_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Název objektu třídy, které definujete jako neagregovatelný.  
  
### <a name="remarks"></a>Poznámky  
 Způsobí, že DECLARE_NOT_AGGREGATABLE `CreateInstance` pro vrácení chyby (CLASS_E_NOAGGREGATION), pokud je proveden pokus o agregaci na objekt.  
  
 Ve výchozím nastavení [CComCoClass](../../atl/reference/ccomcoclass-class.md) obsahuje [DECLARE_AGGREGATABLE](#declare_aggregatable) makra, která určuje, že objekt se dají agregovat. Chcete-li přepsat toto výchozí chování, zahrnují DECLARE_NOT_AGGREGATABLE v definici třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]  
  
##  <a name="declare_only_aggregatable"></a>  DECLARE_ONLY_AGGREGATABLE  
 Určuje, zda váš objekt musí být agregován.  
  
```
DECLARE_ONLY_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Název objektu třídy, které definujete jako pouze agregovatelné.  
  
### <a name="remarks"></a>Poznámky  
 DECLARE_ONLY_AGGREGATABLE způsobí chybu (E_FAIL), pokud je proveden pokus o `CoCreate` objektu jako neagregovaná objektu.  
  
 Ve výchozím nastavení [CComCoClass](../../atl/reference/ccomcoclass-class.md) obsahuje [DECLARE_AGGREGATABLE](#declare_aggregatable) makra, která určuje, že objekt se dají agregovat. Chcete-li přepsat toto výchozí chování, zahrnují DECLARE_ONLY_AGGREGATABLE v definici třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]  
  
##  <a name="declare_poly_aggregatable"></a>  DECLARE_POLY_AGGREGATABLE  
 Určuje, že instance **CComPolyObject \<**  *x* **>** se vytvoří při vytvoření objektu.  
  
```
DECLARE_POLY_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Název objektu třídy, které definujete jako agregovatelné nebo neagregovatelný.  
  
### <a name="remarks"></a>Poznámky  
 Při vytváření se kontroluje hodnota vnější neznámá. Pokud má hodnotu NULL, `IUnknown` je implementován pro neagregovaná objektu. Pokud není NULL, vnější Neznámá `IUnknown` je implementován pro agregovaného objektu.  
  
 Výhodou použití DECLARE_POLY_AGGREGATABLE je, že se vyhnete nutnosti obě `CComAggObject` a `CComObject` v modulu pro zpracování agregované a neagregovaná případech. Jediný `CComPolyObject` objekt zpracovává obou případech. To znamená, že existují jenom jednu kopii tabulku vtable a jedna kopie funkce v modulu. Pokud je vaše vtable velký, to může výrazně zkrátit velikost vašeho modulu. Nicméně pokud je vaše vtable malá, pomocí `CComPolyObject` může vést o něco větší velikost modulu, protože není optimalizován pro objekt agregována nebo neagregovaná jsou `CComAggObject` a `CComObject`.  
  
 – Makro DECLARE_POLY_AGGREGATABLE je automaticky deklarované v objektu, pokud použijete Průvodce ovládacími prvky ATL k vytvoření úplné řízení.  
  
##  <a name="declare_protect_final_construct"></a>  DECLARE_PROTECT_FINAL_CONSTRUCT  

 Chrání váš objekt odstranit, pokud (během [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) interní agregovaného objektu zvýší počet odkazů pak dekrementuje počet na hodnotu 0.  
  
```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```  
  
##  <a name="declare_view_status"></a>  DECLARE_VIEW_STATUS  
 Toto makro umístěte ovládací prvek ActiveX knihovny ATL třídy ovládacího prvku k určení, které příznaky do kontejneru.  
  
```
DECLARE_VIEW_STATUS( statusFlags )
```  
  
### <a name="parameters"></a>Parametry  
 *statusFlags*  
 [in] KTERÉ příznaky. Zobrazit [které](http://msdn.microsoft.com/library/windows/desktop/ms687201) seznam příznaky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)
