# イキヅライブ聖地巡礼マップ

イキヅライブ！ LOVELIVE! BLUEBIRDの聖地情報をまとめた非公式サイトです。

# Requirements

Nix

direnv

# Install

direnvを有効化してDevShellに入ります。

```bash
direnv allow
```

依存パッケージをインストールします。

```bash
bun i
```

開発サーバーを起動します。

```bash
bun run dev
```

# Contribution

./public/data.jsonを編集することで聖地情報を編集することができます。

追加、誤りの訂正などがありましたら、お気軽にIssueやPRでご報告ください。

JSONはこのスキーマでバリデーションされます。

```typescript
export const Data = z.object({
	title: z.string(),
	color: z.string(),
	about: z.string(),
	author: z.string(),
	authorLink: z.string(),
	links: z.array(z.string()),
	spots: z.array(Spot),
});

export const Spot = z.object({
  name: z.string(),
  latLng: z.array(z.number()).length(2),
  description: z.string(),
  images: z.array(z.string()).optional(),
  district: z.string().optional(),
});
```

`images`にはURLの配列を入力してください。`district`を省略した場合は、国土地理院のAPIから自動で補完されます。

# License

MIT
