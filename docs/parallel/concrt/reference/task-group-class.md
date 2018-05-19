`task_group` Třída reprezentuje kolekci paralelní práce, která může být čekali nebo došlo ke zrušení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class task_group;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[task_group](#ctor)|Přetíženo. Vytvoří nový `task_group` objektu.|  
|[~ task_group – destruktor](#dtor)|Zničí `task_group` objektu. Předpokládá se, že buď volání `wait` nebo `run_and_wait` metoda pro objekt před destruktor provádění, pokud je destruktor je prováděna v důsledku kvůli výjimce unwinding zásobníku.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Zrušit](#cancel)|Díky usilovně pokus o zrušení podstromu pracovní root v této skupině úloh. Každý úkol naplánovat na skupině úloh bude získat zrušena přechodně Pokud je to možné.|  
|[is_canceling –](#is_canceling)|Informuje o volající, jestli je skupina úkolů aktuálně in the midst of zrušení. To nemusí znamenat, který `cancel` byla volána metoda `task_group` objektu (i když například tato metoda vrátí vyfiltrování určitě `true`). Může být tento případ, `task_group` objektu provádí vložené a další skupinu úkolů až ve stromové struktuře pracovní byla zrušena. V případech, například tyto kde můžete určit modulu runtime dopředu, který zrušení bude procházet přes tento `task_group` objekt, `true` bude vrácen také.|  
|[Spustit](#run)|Přetíženo. Naplánuje úlohu na `task_group` objektu. Pokud `task_handle` objekt je předán jako parametr, který se `run`, volající zodpovídá za správu životnost `task_handle` objektu. Provedení menší také než použití verzi, která vytvoří odkaz na verzi metody, která přijímá odkaz na objekt funkce, jako parametr zahrnuje přidělení haldy uvnitř modul runtime, který může být `task_handle` objektu. Verze, která přebírá parametr `_Placement` úlohu být tendenční směrem k provádění v umístění zadaném hodnotou tohoto parametru.|  
|[run_and_wait](#run_and_wait)|Přetíženo. Plány úlohy ke spuštění vložené na kontext volání s pomocí `task_group` objekt pro podporu úplné zrušení. Funkce pak čeká, dokud všechny práci `task_group` objekt buď dokončit nebo byla zrušena. Pokud `task_handle` objekt je předán jako parametr, který se `run_and_wait`, volající zodpovídá za správu životnost `task_handle` objektu.|  
|[Počkej](#wait)|Čeká, dokud všechny práci `task_group` objekt buď dokončit nebo byla zrušena.|  
  
## <a name="remarks"></a>Poznámky  
 Na rozdíl od výraznou omezené `structured_task_group` třídy, `task_group` třída je mnohem víc obecné konstrukce. Nemá žádné omezení popsaného [structured_task_group](structured-task-group-class.md). `task_group` objekty může bezpečně používané v rámci celé vláken a využitím volného tvaru. Nevýhodou `task_group` konstrukce je, že nemusí provádět společně s `structured_task_group` vytvořit pro úlohy, které provedení malé množství práce.  
  
 Další informace najdete v tématu [paralelismus](../task-parallelism-concurrency-runtime.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `task_group`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppl.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="cancel"></a> Zrušit 

 Díky usilovně pokus o zrušení podstromu pracovní root v této skupině úloh. Každý úkol naplánovat na skupině úloh bude získat zrušena přechodně Pokud je to možné.  
  
```  
void cancel();  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [zrušení](../cancellation-in-the-ppl.md).  
  
##  <a name="is_canceling"></a> is_canceling – 

 Informuje o volající, jestli je skupina úkolů aktuálně in the midst of zrušení. To nemusí znamenat, který `cancel` byla volána metoda `task_group` objektu (i když například tato metoda vrátí vyfiltrování určitě `true`). Může být tento případ, `task_group` objektu provádí vložené a další skupinu úkolů až ve stromové struktuře pracovní byla zrušena. V případech, například tyto kde můžete určit modulu runtime dopředu, který zrušení bude procházet přes tento `task_group` objekt, `true` bude vrácen také.  
  
```  
bool is_canceling();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Sdělení, zda `task_group` objektu je in the midst of zrušení (nebo záruku, že být zanedlouho).  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [zrušení](../cancellation-in-the-ppl.md).  
  
##  <a name="run"></a> Spustit 

 Naplánuje úlohu na `task_group` objektu. Pokud `task_handle` objekt je předán jako parametr, který se `run`, volající zodpovídá za správu životnost `task_handle` objektu. Provedení menší také než použití verzi, která vytvoří odkaz na verzi metody, která přijímá odkaz na objekt funkce, jako parametr zahrnuje přidělení haldy uvnitř modul runtime, který může být `task_handle` objektu. Verze, která přebírá parametr `_Placement` úlohu být tendenční směrem k provádění v umístění zadaném hodnotou tohoto parametru.  
  
```  
template<  
   typename _Function  
>  
void run(  
   const _Function& _Func  
);  
  
template<  
   typename _Function  
>  
void run(  
   const _Function& _Func,  
   location& _Placement  
);  
  
template<  
   typename _Function  
>  
void run(  
   task_handle<_Function>& _Task_handle  
);  
  
template<  
   typename _Function  
>  
void run(  
   task_handle<_Function>& _Task_handle,  
   location& _Placement  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ objektu funkce, která bude volána provést text popisovač úloh.  
  
 `_Func`  
 Funkci, která bude volána k vyvolání text úlohy. To může být výraz lambda nebo jiného objektu, která podporuje verzi operátor volání funkce s podpisem `void operator()()`.  
  
 `_Placement`  
 Odkaz na umístění, kde úloha reprezentována `_Func` parametr má být spuštěn.  
  
 `_Task_handle`  
 Popisovač pro pracovní naplánován. Všimněte si, že má volající odpovědnost za dobu životnosti tohoto objektu. Modul runtime bude pokračovat očekávat, že za provozu, dokud buď `wait` nebo `run_and_wait` byla volána metoda v tomto `task_group` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime naplánuje zadaná pracovní funkce spustit později, což může být po volání funkce vrátí hodnotu. Tato metoda používá [task_handle](task-handle-class.md) objekt pro uložení kopie zadaná pracovní funkce. Proto se v vaší kopie tohoto objektu funkce nezobrazí žádné změny stavu v objektu funkce, kterou předáte této metodě. Kromě toho se ujistěte, že doba platnosti objektů, které předáte ukazatel nebo odkaz na tuto funkci pracovní zůstává v platnosti, do pracovní funkce vrátí hodnotu.  
  
 Pokud `task_group` destructs v důsledku z výjimku unwinding zásobníku, není nutné zaručit, že volání nebyly provedeny buď `wait` nebo `run_and_wait` metoda. V takovém případě destruktoru správně zruší a čekání na úlohu reprezentována `_Task_handle` parametr k dokončení.  
  
 Vyvolá metoda [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) výjimka, pokud úloha zpracovat dané podle `_Task_handle` parametr již bylo naplánováno na objekt úlohy skupiny prostřednictvím `run` metoda a došlo žádné uplynulého volání buď `wait` nebo `run_and_wait` metoda na této skupině úloh.  
  
##  <a name="run_and_wait"></a> run_and_wait – 

 Plány úlohy ke spuštění vložené na kontext volání s pomocí `task_group` objekt pro podporu úplné zrušení. Funkce pak čeká, dokud všechny práci `task_group` objekt buď dokončit nebo byla zrušena. Pokud `task_handle` objekt je předán jako parametr, který se `run_and_wait`, volající zodpovídá za správu životnost `task_handle` objektu.  
  
```  
template<  
   class _Function  
>  
task_group_status run_and_wait(  
   task_handle<_Function>& _Task_handle  
);  
  
template<  
   class _Function  
>  
task_group_status run_and_wait(  
   const _Function& _Func  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ objektu funkce, která bude volána k provedení text úlohy.  
  
 `_Task_handle`  
 Popisovač pro úlohu, která se spustí vložené na kontext volání. Všimněte si, že má volající odpovědnost za dobu životnosti tohoto objektu. Modul runtime bude pokračovat očekávat, že za provozu, dokud `run_and_wait` metoda dokončí provádění.  
  
 `_Func`  
 Funkci, která bude volána k vyvolání text práce. To může být výraz lambda nebo jiného objektu, která podporuje verzi operátor volání funkce s podpisem `void operator()()`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Údaj o tom, zda byla splněna čekání nebo skupině úloh byla zrušena, z důvodu operace explicitní zrušit nebo výjimku hlášeny z jednoho z jeho úlohy. Další informace najdete v tématu [task_group_status](concurrency-namespace-enums.md#task_group_status).  

  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že jeden nebo více úloh naplánovaných k tomuto `task_group` objekt může spustit vložené na kontext volání.  
  
 Pokud jeden nebo více úloh naplánovaných k tomuto `task_group` objekt vyvolá výjimku, použije modul runtime vyberte jeden takové výjimky jeho výběru a šířit z volání `run_and_wait` metoda.  
  
 Po návratu z `run_and_wait` metodu `task_group` objektu modulu runtime obnoví objekt do čistého stavu, kde ji můžete znovu použít. To zahrnuje i situace, kde `task_group` objekt byl zrušen.  
  
 V cestě k ostatním provádění, máte pověření k volání této metody nebo `wait` metody před destruktoru objektu `task_group` provede.  
  
##  <a name="ctor"></a> task_group 

 Vytvoří nový `task_group` objektu.  
  
```  
task_group();  
  
task_group(  
   cancellation_token _CancellationToken  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_CancellationToken`  
 Token zrušení pro přidružit k této skupině úloh. Když je zrušeno token, budou zrušeny skupiny úloh.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor, který přebírá token zrušení vytvoří `task_group` , budou zrušeny, když se zruší zdrojový přidružené k tokenu. Token zrušení explicitní poskytuje také izoluje této skupiny úloh ze implicitní zrušení z nadřazené skupiny s token jiné nebo žádné token.  
  
##  <a name="dtor"></a> ~ task_group 

 Zničí `task_group` objektu. Předpokládá se, že buď volání `wait` nebo `run_and_wait` metoda pro objekt před destruktor provádění, pokud je destruktor je prováděna v důsledku kvůli výjimce unwinding zásobníku.  
  
```  
~task_group();  
```  
  
### <a name="remarks"></a>Poznámky  
 Jestliže destruktoru běží jako výsledek normální spuštění (například není unwinding zásobníku kvůli výjimce) a ani `wait` ani `run_and_wait` metod, může vyvolat destruktoru [missing_wait](missing-wait-class.md) došlo k výjimce.  
  
##  <a name="wait"></a> Počkej 

 Čeká, dokud všechny práci `task_group` objekt buď dokončit nebo byla zrušena.  
  
```  
task_group_status wait();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Údaj o tom, zda byla splněna čekání nebo skupině úloh byla zrušena, z důvodu operace explicitní zrušit nebo výjimku hlášeny z jednoho z jeho úlohy. Další informace najdete v tématu [task_group_status](concurrency-namespace-enums.md#task_group_status).  

  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že jeden nebo více úloh naplánovaných k tomuto `task_group` objekt může spustit vložené na kontext volání.  
  
 Pokud jeden nebo více úloh naplánovaných k tomuto `task_group` objekt vyvolá výjimku, použije modul runtime vyberte jeden takové výjimky jeho výběru a šířit z volání `wait` metoda.  
  
 Volání metody `wait` na `task_group` objekt se obnoví do čistého stavu, kde ji můžete znovu použít. To zahrnuje i situace, kde `task_group` objekt byl zrušen.  
  
 V cestě k ostatním provádění, máte pověření k volání této metody nebo `run_and_wait` metody před destruktoru objektu `task_group` provede.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [structured_task_group – třída](structured-task-group-class.md)   
 [task_handle – třída](task-handle-class.md)