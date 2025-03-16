# medusav2-file-supabase-storage

A custom file storage provider for Medusa v2 using Supabase Storage. This plugin allows you to store and manage media files in a Supabase bucket, integrating seamlessly with Medusa's file provider service.

## Features

- Upload files to a Supabase storage bucket.
- Retrieve public URLs for uploaded files.
- Delete files from Supabase storage.
- Uses Supabase's storage API for seamless integration.

## Installation

```sh
npm install medusav2-file-supabase-storage
```

## Configuration

To use this plugin in your Medusa v2 project, configure it in your Medusa backend.

### Medusa Plugin Configuration

Update your `medusa-config.js` or similar configuration file to include the `medusav2-supabase-storage` provider:

```js
const plugins = [
  {
    resolve: "medusav2-file-supabase-storage/modules/file",
    options: {
      apiKey: "your-supabase-api-key",
      supabaseUrl: "your-supabase-url",
      bucketName: "your-bucket-name",
    },
  },
];

module.exports = { plugins };
```

## Usage

### Upload a File

The provider uploads files to the specified Supabase storage bucket.

```ts
const file = {
  filename: "example.png",
  content: Buffer.from("file-content", "binary"),
  mimeType: "image/png",
};

const result = await fileProvider.upload(file);
console.log(result.url); // Public URL of the uploaded file
```

### Delete a File

To delete a file from Supabase storage:

```ts
await fileProvider.delete({ fileKey: "example.png" });
```

## Development

If you want to modify or extend this plugin:

1. Clone the repository.
2. Install dependencies.
3. Implement additional features as needed.

## License

This project is licensed under the MIT License.

---

### Notes
- Ensure your Supabase bucket is configured to allow public access if you need public URLs.
- The `upload` method prevents overwriting existing files by default (upsert: false).

