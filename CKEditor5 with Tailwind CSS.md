
Unless doing something, Tailwind CSS 'clears' styles of CKEditor. To style CKEditor properly, do the followings:

1. Install `@tailwindcss/typography`

```sh
npm install @tailwindcss/typography
```

2. Wrap the CKEditor component with `prose` class

```jsx
<div className="prose max-w-full">
  <CKEditor {...editorProps} />
</div>
```