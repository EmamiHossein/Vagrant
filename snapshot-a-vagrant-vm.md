# Snapshot a Vagrant VM as a Reusable Box

This guide explains how to export a configured Vagrant virtual machine as a reusable box (template). This is useful when you've installed all necessary packages and want to reuse the same environment in other projects without repeating setup steps.

## Example: Exporting `bento/rockylinux-9.5`

We’ll use a VM based on `bento/rockylinux-9.5` as an example.

---

## Steps

### 1. Halt the running VM

Navigate to your project directory and halt the VM:

```bash
vagrant halt
```

---

### 2. Package the VM into a `.box` file

```bash
vagrant package --output rocky9-template.box
```

This command creates a file named `rocky9-template.box` in your current directory.

---

### 3. Add the box to Vagrant's local box list

```bash
vagrant box add --name rocky9-template ./rocky9-template.box
```

This adds the box under the name `rocky9-template` so you can use it in other projects.

---

### 4. Verify the box was added

```bash
vagrant box list
```

You should see `rocky9-template` listed among your available boxes.

---

### 5. Update your `Vagrantfile` to use the new box

In your new or existing Vagrant projects, update the box name:

```ruby
config.vm.box = "rocky9-template"
```
