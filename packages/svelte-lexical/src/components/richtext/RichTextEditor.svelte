<script>
  import pkgLRT from '@lexical/rich-text';
  import { ListItemNode, ListNode } from '@lexical/list';
  import TextEditor from '../../core/TextEditor.svelte';
  import RichTextPlugin from '../../core/plugins/RichTextPlugin.svelte';
  import HistoryPlugin from '../../core/plugins/HistoryPlugin.svelte';
  import ListPlugin from '../../core/plugins/ListPlugin.svelte';
  import { HorizontalRuleNode } from '../../core/plugins/HorizontalRuleNode';

  import HorizontalRulePlugin from '../../core/plugins/HorizontalRulePlugin.svelte';
  import ImagePlugin from '../../core/plugins/ImagePlugin.svelte';
  import { ImageNode } from '../../core/plugins/ImageNode';

  const { HeadingNode, QuoteNode } = pkgLRT;

  export let theme;

  const config = {
    theme,
    nodes: [
      HeadingNode,
      ListNode,
      ListItemNode,
      QuoteNode,
      HorizontalRuleNode,
      ImageNode,
    ],
    onError: (error) => {
      throw error;
    },
  };
</script>

<TextEditor {config}>
  <slot name="toolbar" slot="toolbar" />
  <RichTextPlugin />
  <HistoryPlugin />
  <ListPlugin />
  <HorizontalRulePlugin />
  <ImagePlugin />
  <slot name="actions" slot="actions" />
</TextEditor>
