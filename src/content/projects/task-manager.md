---
title: "Task Manager App"
description: "A modern task management application built with React and TypeScript, featuring drag-and-drop, real-time sync, and offline support."
publishDate: 2024-01-10
tags: ["react", "typescript", "tailwind"]
github: "https://github.com/yourusername/task-manager"
link: "https://task-manager-demo.netlify.app"
---

# Task Manager App

A full-featured task management application designed for individual productivity and team collaboration.

## Features

- **Drag & Drop**: Intuitive task organization with drag-and-drop interface
- **Real-time Sync**: Changes sync instantly across devices
- **Offline Support**: Full functionality even without internet connection
- **Smart Lists**: Dynamic lists with filters and custom views
- **Collaboration**: Share lists and assign tasks to team members

## Tech Stack

- **Frontend**: React 18, TypeScript, Tailwind CSS
- **State Management**: Zustand with persistence
- **Backend**: Supabase (PostgreSQL, Auth, Realtime)
- **Deployment**: Netlify with continuous deployment

## Key Learnings

Building this project taught me:

1. Implementing optimistic updates for better UX
2. Managing offline state with service workers
3. Real-time collaboration with WebSockets
4. Complex state management patterns
5. Performance optimization for large lists

## Implementation Highlights

### Drag and Drop

Used `@dnd-kit` for accessible, performant drag-and-drop:

```typescript
import { DndContext, closestCenter } from '@dnd-kit/core';
import { SortableContext, verticalListSortingStrategy } from '@dnd-kit/sortable';

function TaskList({ tasks }: Props) {
  const handleDragEnd = (event: DragEndEvent) => {
    // Update task order
  };

  return (
    <DndContext collisionDetection={closestCenter} onDragEnd={handleDragEnd}>
      <SortableContext items={tasks} strategy={verticalListSortingStrategy}>
        {tasks.map(task => <TaskItem key={task.id} task={task} />)}
      </SortableContext>
    </DndContext>
  );
}
```

### Offline Support

Implemented a sync queue for offline operations:

```typescript
class SyncQueue {
  private queue: Operation[] = [];

  async add(operation: Operation) {
    this.queue.push(operation);
    await this.persist();
    if (navigator.onLine) {
      await this.flush();
    }
  }

  async flush() {
    while (this.queue.length > 0) {
      const op = this.queue[0];
      await this.execute(op);
      this.queue.shift();
      await this.persist();
    }
  }
}
```

## Future Enhancements

- [ ] Mobile apps (React Native)
- [ ] Calendar integration
- [ ] Email notifications
- [ ] Advanced analytics
- [ ] AI-powered task suggestions

## Links

- [Live Demo](https://task-manager-demo.netlify.app)
- [GitHub Repository](https://github.com/yourusername/task-manager)
