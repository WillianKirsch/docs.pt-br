### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a><span data-ttu-id="0be8e-101">Evento SelectionChanged e propriedade SelectedValue do seletor</span><span class="sxs-lookup"><span data-stu-id="0be8e-101">Selector SelectionChanged event and SelectedValue property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0be8e-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="0be8e-102">Details</span></span>|<span data-ttu-id="0be8e-103">Começando com o .NET Framework 4.7.1, um <xref:System.Windows.Controls.Primitives.Selector> sempre atualiza o valor de sua propriedade <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> antes de acionar o evento <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>, quando sua seleção é alterada.</span><span class="sxs-lookup"><span data-stu-id="0be8e-103">Starting with the .NET Framework 4.7.1, a <xref:System.Windows.Controls.Primitives.Selector> always updates the value of its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property before raising the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event, when its selection changes.</span></span> <span data-ttu-id="0be8e-104">Isso torna a propriedade SelectedValue consistente com as outras propriedades de seleção (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> e <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), que são atualizadas antes que o evento seja acionado.</span><span class="sxs-lookup"><span data-stu-id="0be8e-104">This makes the SelectedValue property consistent with the other selection properties (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> and <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), which are updated before raising the event.</span></span><p/><span data-ttu-id="0be8e-105">No .NET Framework 4.7 e nas versões anteriores, a atualização de SelectedValue ocorria antes do evento na maioria dos casos, mas ocorria depois do evento quando a alteração da seleção era causada pela alteração da propriedade <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="0be8e-105">In the .NET Framework 4.7 and earlier versions, the update to SelectedValue happened before the event in most cases, but it happened after the event if the selection change was caused by changing the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>|
|<span data-ttu-id="0be8e-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="0be8e-106">Suggestion</span></span>|<span data-ttu-id="0be8e-107">Aplicativos destinados ao .NET Framework 4.7.1 ou posteriores podem recusar essa alteração e usar o comportamento herdado adicionando o seguinte à seção <code>&lt;runtime&gt;</code> do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="0be8e-107">Apps that target the .NET Framework 4.7.1 or later can opt out of this change and use legacy behavior by adding the following to the <code>&lt;runtime&gt;</code> section of the application configuration file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre><span data-ttu-id="0be8e-108">Aplicativos destinados ao .NET Framework 4.7 ou anteriores, mas que são executados no .NET Framework 4.7.1 ou posteriores podem habilitar o novo comportamento adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="0be8e-108">Apps that target the .NET Framework 4.7 or earlier but are running on the .NET Framework 4.7.1 or later can enable the new behavior by adding the following line to the <code>&lt;runtime&gt;</code> section of the application .configuration file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="0be8e-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="0be8e-109">Scope</span></span>|<span data-ttu-id="0be8e-110">Secundário</span><span class="sxs-lookup"><span data-stu-id="0be8e-110">Minor</span></span>|
|<span data-ttu-id="0be8e-111">Versão</span><span class="sxs-lookup"><span data-stu-id="0be8e-111">Version</span></span>|<span data-ttu-id="0be8e-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="0be8e-112">4.7.1</span></span>|
|<span data-ttu-id="0be8e-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="0be8e-113">Type</span></span>|<span data-ttu-id="0be8e-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="0be8e-114">Retargeting</span></span>|
|<span data-ttu-id="0be8e-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0be8e-115">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|
