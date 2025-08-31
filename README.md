# PCG
PCG Dashboard
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Myworkspace</title>
    <style>
        /* Reset and base styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: #0f1419;
            color: #e2e8f0;
            line-height: 1.6;
            min-height: 100vh;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Header styles */
        header {
            background: linear-gradient(135deg, #1e3a8a 0%, #dc2626 100%);
            border-radius: 12px;
            padding: 20px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.5);
        }

        header h1 {
            font-size: 1.8rem;
            color: white;
        }

        .subtitle {
            font-size: 0.9rem;
            opacity: 0.9;
            color: white;
        }

        .vault-btn {
            background: rgba(255,255,255,0.2);
            color: white;
            border: 1px solid rgba(255,255,255,0.3);
            padding: 10px 20px;
            border-radius: 8px;
            cursor: pointer;
            position: relative;
            transition: all 0.3s;
        }

        .vault-btn:hover {
            background: rgba(255,255,255,0.3);
        }

        .vault-badge {
            position: absolute;
            top: -8px;
            right: -8px;
            background: #dc2626;
            color: #fff;
            font-size: 0.75rem;
            font-weight: 700;
            padding: 2px 8px;
            border-radius: 20px;
            min-width: 24px;
            text-align: center;
        }

        /* Stats bar */
        .stats-bar {
            background: #1a2332;
            border-radius: 8px;
            padding: 16px;
            margin-bottom: 20px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 16px;
            border: 1px solid #2d3f57;
        }

        .stat-item {
            text-align: center;
        }

        .stat-value {
            font-size: 1.8rem;
            font-weight: 700;
            color: #e2e8f0;
        }

        .stat-label {
            font-size: 0.8rem;
            color: #94a3b8;
        }

        /* Navigation tabs */
        nav {
            background: #1a2332;
            border-radius: 12px;
            margin-bottom: 20px;
            display: flex;
            overflow: hidden;
            border: 1px solid #2d3f57;
        }

        .tab {
            flex: 1;
            text-align: center;
            padding: 14px 20px;
            cursor: pointer;
            border-bottom: 4px solid transparent;
            transition: all 0.2s;
            color: #e2e8f0;
        }

        .tab:hover {
            background: #243447;
        }

        .tab.active {
            border-bottom-color: #2563eb;
            background: #243447;
            font-weight: 700;
        }

        /* Panel styles */
        .panel {
            display: none;
        }

        .panel.active {
            display: block;
        }

        .panel-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .panel-header h2 {
            color: #e2e8f0;
            font-size: 1.5rem;
        }

        .add-btn {
            background: linear-gradient(135deg, #10b981 0%, #059669 100%);
            color: #fff;
            border: none;
            padding: 10px 18px;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s;
        }

        .add-btn:hover {
            transform: translateY(-1px);
            box-shadow: 0 4px 12px rgba(16, 185, 129, 0.3);
        }

        /* Grid layout */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(380px, 1fr));
            gap: 20px;
        }

        /* Card styles */
        .card {
            background: #1a2332;
            border-radius: 14px;
            padding: 24px;
            padding-top: 50px;
            position: relative;
            box-shadow: 0 2px 6px rgba(0,0,0,0.4);
            border: 1px solid #2d3f57;
            transition: all 0.2s;
        }

        .card:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(0,0,0,0.5);
            border-color: #3b82f6;
        }

        .card h3 {
            font-size: 1.1rem;
            color: #e2e8f0;
            margin-bottom: 10px;
            padding-right: 40px;
        }

        .card p {
            color: #cbd5e1;
            font-size: 0.9rem;
            margin-bottom: 15px;
        }

        /* Priority badge */
        .priority-badge {
            position: absolute;
            top: 12px;
            left: 12px;
            padding: 6px 12px;
            border-radius: 6px;
            font-size: 0.75rem;
            font-weight: 600;
        }

        .priority-high {
            background: #dc2626;
            color: #fff;
        }

        .priority-medium {
            background: #f59e0b;
            color: #fff;
        }

        .priority-low {
            background: #10b981;
            color: #fff;
        }

        /* Delete button */
        .del {
            position: absolute;
            top: 12px;
            right: 12px;
            background: #dc2626;
            border: none;
            width: 36px;
            height: 36px;
            border-radius: 8px;
            color: #fff;
            cursor: pointer;
            font-size: 1.1rem;
        }

        .del:hover {
            background: #ef4444;
        }

        /* Status tags */
        .status-tags {
            display: flex;
            gap: 6px;
            margin-bottom: 10px;
            flex-wrap: wrap;
        }

        .status-tag {
            font-size: 0.7rem;
            padding: 3px 8px;
            border-radius: 6px;
            font-weight: 600;
        }

        .tag-at {
            background: #dc2626;
            color: #fff;
        }

        .tag-ac {
            background: #2563eb;
            color: #fff;
        }

        .tag-integrated {
            background: #7c3aed;
            color: #fff;
        }

        .tag-commercial {
            background: #059669;
            color: #fff;
        }

        .tag-personal {
            background: #8b5cf6;
            color: #fff;
        }

        /* Actions */
        .actions {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-top: 10px;
        }

        .pill {
            border: none;
            border-radius: 6px;
            padding: 8px 14px;
            font-size: 0.8rem;
            cursor: pointer;
            transition: all 0.2s;
            font-weight: 500;
        }

        .blue {
            background: #2563eb;
            color: #fff;
        }

        .blue:hover {
            background: #1d4ed8;
        }

        .green {
            background: #10b981;
            color: #fff;
        }

        .green:hover {
            background: #059669;
        }

        .purple {
            background: #7c3aed;
            color: #fff;
        }

        .purple:hover {
            background: #6d28d9;
        }

        .red {
            background: #dc2626;
            color: #fff;
        }

        .red:hover {
            background: #ef4444;
        }

        /* Modal styles */
        .overlay {
            position: fixed;
            inset: 0;
            background: rgba(0, 0, 0, 0.8);
            display: flex;
            align-items: center;
            justify-content: center;
            visibility: hidden;
            opacity: 0;
            transition: opacity 0.2s, visibility 0.2s;
            z-index: 1000;
        }

        .overlay.show {
            visibility: visible;
            opacity: 1;
        }

        .modal {
            background: #2a303c;
            border-radius: 16px;
            width: 90%;
            max-width: 560px;
            padding: 32px;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
        }

        .modal h3 {
            color: #ffffff;
            margin-bottom: 24px;
            font-size: 1.5rem;
            font-weight: 400;
        }

        .modal input,
        .modal textarea,
        .modal select {
            width: 100%;
            padding: 16px;
            margin-bottom: 20px;
            border: 1px solid #3d4451;
            border-radius: 12px;
            background: #1f2937;
            color: #e2e8f0;
            font-size: 1rem;
            transition: all 0.2s;
        }

        .modal input:focus,
        .modal textarea:focus,
        .modal select:focus {
            outline: none;
            border-color: #3b82f6;
            background: #262e3e;
        }

        .modal textarea {
            resize: vertical;
            min-height: 100px;
        }

        .modal label {
            display: block;
            margin-bottom: 12px;
            color: #e2e8f0;
            font-size: 1.1rem;
            font-weight: 400;
        }

        /* Button styles */
        .btn {
            background: #3d4451;
            color: #e2e8f0;
            border: none;
            padding: 12px 24px;
            border-radius: 10px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 500;
            transition: all 0.2s;
        }

        .btn:hover {
            background: #4a5568;
        }

        .btn-primary {
            background: #3b82f6;
            color: white;
        }

        .btn-primary:hover {
            background: #2563eb;
        }

        /* Priority selector */
        .priority-selector {
            display: flex;
            gap: 12px;
            margin-bottom: 24px;
        }

        .priority-option {
            flex: 1;
            padding: 16px;
            border: 2px solid #3d4451;
            border-radius: 12px;
            text-align: center;
            cursor: pointer;
            transition: all 0.2s;
            background: #1f2937;
            color: #e2e8f0;
            font-size: 1.1rem;
            font-weight: 500;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .priority-option:hover {
            border-color: #4a5568;
            background: #262e3e;
        }

        .priority-option.selected {
            border-color: #3b82f6;
            background: #3b82f6;
            color: white;
        }

        .priority-indicator {
            width: 20px;
            height: 20px;
            border-radius: 50%;
            display: inline-block;
        }

        .priority-high .priority-indicator {
            background: #dc2626;
        }

        .priority-medium .priority-indicator {
            background: #f59e0b;
        }

        .priority-low .priority-indicator {
            background: #10b981;
        }

        /* Links section */
        .links-section {
            margin-bottom: 24px;
        }

        .link-input-group {
            display: flex;
            gap: 12px;
            margin-bottom: 16px;
        }

        .link-input-group input {
            flex: 1;
            margin-bottom: 0;
        }

        .add-link-btn {
            background: #3b82f6;
            color: white;
            border: none;
            width: 48px;
            height: 48px;
            border-radius: 10px;
            cursor: pointer;
            font-size: 1.5rem;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.2s;
        }

        .add-link-btn:hover {
            background: #2563eb;
        }

        .links-list {
            margin-top: 12px;
        }

        .link-item {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 8px 12px;
            background: #1f2937;
            border-radius: 8px;
            margin-bottom: 8px;
            color: #94a3b8;
            font-size: 0.9rem;
        }

        .link-item button {
            background: transparent;
            border: none;
            color: #dc2626;
            cursor: pointer;
            font-size: 1.2rem;
            padding: 4px;
        }

        .link-item button:hover {
            color: #ef4444;
        }

        /* File upload section */
        .file-upload-section {
            margin-top: 24px;
            padding-top: 24px;
            border-top: 1px solid #3d4451;
        }

        .file-upload-label {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 16px;
            color: #e2e8f0;
            font-size: 1.1rem;
        }

        .file-upload-btn {
            background: #e2e8f0;
            color: #1f2937;
            border: none;
            padding: 12px 24px;
            border-radius: 10px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 500;
            transition: all 0.2s;
            display: inline-block;
        }

        .file-upload-btn:hover {
            background: #cbd5e1;
        }

        .file-count {
            color: #94a3b8;
            margin-left: 12px;
        }

        .modal-actions {
            display: flex;
            gap: 16px;
            justify-content: flex-end;
            margin-top: 32px;
            padding-top: 24px;
            border-top: 1px solid #3d4451;
        }

        /* Notification */
        .notification {
            position: fixed;
            top: 60px;
            right: 20px;
            background: #10b981;
            color: #fff;
            padding: 12px 20px;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
            opacity: 0;
            transform: translateY(-20px);
            transition: all 0.3s;
            z-index: 1200;
        }

        .notification.show {
            opacity: 1;
            transform: translateY(0);
        }

        /* Overview styles */
        .quick-actions {
            display: flex;
            gap: 12px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }

        .quick-action-btn {
            background: linear-gradient(135deg, #1e3a8a 0%, #1e40af 100%);
            color: #fff;
            border: none;
            padding: 10px 20px;
            border-radius: 10px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: all 0.2s;
        }

        .quick-action-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(30, 58, 138, 0.3);
        }

        .quick-action-btn.secondary {
            background: #243447;
            color: #e2e8f0;
        }

        .overview-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 20px;
            margin-bottom: 24px;
        }

        .overview-section {
            background: #1a2332;
            border-radius: 16px;
            border: 1px solid #2d3f57;
            overflow: hidden;
        }

        .overview-section h3 {
            margin: 0;
            padding: 16px 20px;
            font-size: 1rem;
            color: #e2e8f0;
            background: #0f1419;
            border-bottom: 1px solid #2d3f57;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .overview-section h3::after {
            content: attr(data-count);
            font-size: 0.8rem;
            background: #243447;
            padding: 2px 10px;
            border-radius: 12px;
            color: #94a3b8;
        }

        .overview-items {
            padding: 12px;
            max-height: 300px;
            overflow-y: auto;
        }

        .overview-item {
            background: #243447;
            border-radius: 10px;
            padding: 12px 16px;
            margin-bottom: 8px;
            cursor: pointer;
            transition: all 0.2s;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .overview-item:hover {
            background: #2d3f57;
            transform: translateX(4px);
        }

        .overview-item-icon {
            width: 24px;
            height: 24px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .overview-item-content {
            flex: 1;
        }

        .overview-item .pill {
            padding: 4px 8px;
            font-size: 0.7rem;
        }

        .overview-item-meta {
            display: flex;
            gap: 12px;
            font-size: 0.8rem;
            color: #94a3b8;
            margin-top: 4px;
        }

        .overview-empty {
            text-align: center;
            padding: 60px 20px;
            color: #64748b;
        }

        /* HTML Display Area */
        .html-display-area {
            grid-column: 1 / -1;
            background: #1a2332;
            border-radius: 16px;
            border: 1px solid #2d3f57;
            overflow: hidden;
            margin-top: 20px;
            min-height: 400px;
        }

        .html-display-header {
            padding: 16px 20px;
            background: #0f1419;
            border-bottom: 1px solid #2d3f57;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .html-display-header h3 {
            margin: 0;
            font-size: 1rem;
            color: #e2e8f0;
        }

        .html-content-frame {
            width: 100%;
            height: 500px;
            border: none;
            background: #fff;
        }

        .html-empty-state {
            text-align: center;
            padding: 80px 20px;
            color: #64748b;
        }

        .html-empty-icon {
            font-size: 3rem;
            opacity: 0.3;
            margin-bottom: 12px;
        }

        .html-control-btn {
            background: #1a2332;
            border: none;
            padding: 6px 10px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 0.8rem;
            color: #e2e8f0;
            transition: all 0.2s;
        }

        .html-control-btn:hover {
            background: #2d3f57;
        }

        /* HTML paste modal */
        .html-paste-modal {
            background: #1a2332;
            border-radius: 12px;
            width: 90%;
            max-width: 700px;
            padding: 24px;
            border: 1px solid #2d3f57;
        }

        .html-paste-modal textarea {
            width: 100%;
            min-height: 300px;
            padding: 12px;
            border: 2px solid #2d3f57;
            border-radius: 8px;
            font-family: monospace;
            font-size: 14px;
            resize: vertical;
            background: #0f1419;
            color: #e2e8f0;
            margin-bottom: 15px;
        }

        /* File list */
        .file-list {
            margin-top: 12px;
            border-top: 1px solid #2d3f57;
            padding-top: 12px;
        }

        .file-item {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 10px;
            margin-bottom: 8px;
            background: #0f1419;
            border-radius: 8px;
            font-size: 0.85rem;
            gap: 10px;
            color: #e2e8f0;
            border: 1px solid #2d3f57;
        }

        .file-info {
            display: flex;
            align-items: center;
            gap: 8px;
            flex: 1;
        }

        .file-actions {
            display: flex;
            gap: 6px;
        }

        .vault-status {
            font-size: 0.7rem;
            padding: 3px 8px;
            border-radius: 4px;
            background: #1e3a8a;
            color: #93c5fd;
        }

        /* Vault Modal */
        #vaultOverlay {
            z-index: 1100;
        }

        .vault-modal {
            background: #0f1419;
            border-radius: 16px;
            width: 90%;
            max-width: 1200px;
            height: 90vh;
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }

        .vault-header {
            background: linear-gradient(135deg, #1e3a8a 0%, #dc2626 100%);
            color: #fff;
            padding: 24px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .vault-header h2 {
            margin: 0;
            font-size: 1.5rem;
        }

        .vault-close {
            background: rgba(255,255,255,0.2);
            border: none;
            color: #fff;
            width: 36px;
            height: 36px;
            border-radius: 8px;
            font-size: 24px;
            cursor: pointer;
        }

        .vault-close:hover {
            background: rgba(255,255,255,0.3);
        }

        /* Category bar */
        .category-bar {
            background: #1a2332;
            padding: 16px 24px;
            display: flex;
            align-items: center;
            gap: 16px;
            border-bottom: 1px solid #2d3f57;
            overflow-x: auto;
        }

        .category-tabs {
            display: flex;
            gap: 10px;
            flex: 1;
        }

        .category-tab {
            padding: 8px 16px;
            background: #243447;
            border: 2px solid transparent;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 8px;
            font-weight: 500;
            color: #e2e8f0;
            font-size: 0.9rem;
            white-space: nowrap;
        }

        .category-tab:hover {
            background: #2d3f57;
            border-color: #2563eb;
        }

        .category-tab.active {
            background: #2563eb;
            color: white;
            border-color: #2563eb;
        }

        .category-color {
            width: 12px;
            height: 12px;
            border-radius: 50%;
        }

        .add-category-btn {
            padding: 8px 16px;
            background: #10b981;
            color: white;
            border: none;
            border-radius: 20px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 5px;
            font-size: 0.9rem;
            white-space: nowrap;
        }

        .add-category-btn:hover {
            background: #059669;
            transform: translateY(-2px);
        }

        .vault-controls {
            padding: 20px 24px;
            background: #1a2332;
            display: flex;
            gap: 16px;
            align-items: center;
        }

        .vault-search {
            flex: 1;
            position: relative;
        }

        .vault-search input {
            width: 100%;
            padding: 10px 16px;
            border: 1px solid #334155;
            border-radius: 8px;
            background: #0f1419;
            color: #e2e8f0;
            font-size: 0.95rem;
        }

        .vault-filters {
            display: flex;
            gap: 10px;
        }

        .vault-filters select {
            padding: 10px 16px;
            border: 1px solid #334155;
            border-radius: 8px;
            background: #0f1419;
            color: #e2e8f0;
            cursor: pointer;
            font-size: 0.95rem;
        }

        /* Vault stats */
        .vault-stats {
            padding: 20px 24px;
            background: #1a2332;
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 20px;
            border-bottom: 1px solid #2d3f57;
        }

        .vault-stat {
            text-align: center;
        }

        .vault-stat-value {
            display: block;
            font-size: 1.8rem;
            font-weight: 700;
            color: #e2e8f0;
        }

        .vault-stat-label {
            display: block;
            font-size: 0.85rem;
            color: #94a3b8;
            margin-top: 4px;
        }

        .vault-content {
            flex: 1;
            padding: 24px;
            overflow-y: auto;
            background: #0f1419;
        }

        .vault-item {
            background: #243447;
            border: 1px solid #2d3f57;
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 16px;
            display: flex;
            align-items: center;
            gap: 20px;
            transition: all 0.2s;
        }

        .vault-item:hover {
            border-color: #3b82f6;
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(59, 130, 246, 0.2);
        }

        .vault-item-icon {
            width: 56px;
            height: 56px;
            background: #f59e0b;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 28px;
        }

        .vault-item-icon.pdf {
            background: #dc2626;
        }

        .vault-item-icon.html {
            background: #f59e0b;
        }

        .vault-item-info {
            flex: 1;
        }

        .vault-item-name {
            font-weight: 600;
            color: #e2e8f0;
            margin-bottom: 6px;
            font-size: 1.05rem;
        }

        .vault-item-meta {
            font-size: 0.85rem;
            color: #94a3b8;
            display: flex;
            gap: 20px;
        }

        .vault-item-category {
            color: #60a5fa;
        }

        .vault-item-actions {
            display: flex;
            gap: 10px;
        }

        .vault-empty {
            text-align: center;
            padding: 80px 20px;
            color: #94a3b8;
        }

        .vault-empty-icon {
            font-size: 4rem;
            opacity: 0.3;
            margin-bottom: 16px;
        }

        /* File preview */
        .preview-iframe {
            width: 100%;
            height: 600px;
            border: 1px solid #2d3f57;
            border-radius: 8px;
            background: #fff;
        }

        /* Category modal */
        .category-modal {
            background: #1a2332;
            border-radius: 12px;
            width: 90%;
            max-width: 500px;
            padding: 30px;
            border: 1px solid #2d3f57;
        }

        .color-picker {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            margin-bottom: 20px;
        }

        .color-option {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            cursor: pointer;
            border: 3px solid transparent;
            transition: all 0.3s;
        }

        .color-option:hover {
            transform: scale(1.1);
        }

        .color-option.selected {
            border-color: #2563eb;
            box-shadow: 0 0 0 2px #1a2332, 0 0 0 4px #2563eb;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .grid {
                grid-template-columns: 1fr;
            }
            
            .stats-bar {
                grid-template-columns: repeat(2, 1fr);
            }
            
            header {
                flex-direction: column;
                gap: 15px;
                text-align: center;
            }
            
            .vault-stats {
                grid-template-columns: repeat(2, 1fr);
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div>
                <h1>🚌 Myworkspace</h1>
                <div class="subtitle">Collaborative Workspace & Document Hub</div>
            </div>
            <button class="vault-btn" onclick="openVault()">
                📂 Document Vault
                <span class="vault-badge" id="vaultBadge">0</span>
            </button>
        </header>

        <div class="stats-bar">
            <div class="stat-item">
                <div class="stat-value" id="totalItems">0</div>
                <div class="stat-label">Total Items</div>
            </div>
            <div class="stat-item">
                <div class="stat-value" id="activeWorkstreams">0</div>
                <div class="stat-label">Active Workstreams</div>
            </div>
            <div class="stat-item">
                <div class="stat-value" id="activeProjects">0</div>
                <div class="stat-label">Active Projects</div>
            </div>
            <div class="stat-item">
                <div class="stat-value" id="totalDocuments">0</div>
                <div class="stat-label">Documents</div>
            </div>
        </div>

        <nav>
            <div class="tab active" data-type="overview">📊 Overview</div>
            <div class="tab" data-type="workstreams">🔄 Workstreams</div>
            <div class="tab" data-type="projects">🎯 Projects</div>
            <div class="tab" data-type="commercial">💼 Commercial</div>
        </nav>

        <main id="mainContent"></main>

        <!-- Add/Edit Modal -->
        <div class="overlay" id="modalOverlay">
            <div class="modal">
                <h3 id="modalTitle">Edit Workstream</h3>
                
                <input type="text" id="titleInput" placeholder="Enter title" required>
                
                <textarea id="descInput" placeholder="Enter description" rows="4"></textarea>
                
                <label>Priority Level</label>
                <div class="priority-selector">
                    <div class="priority-option priority-high" data-priority="high">
                        <span class="priority-indicator"></span>
                        High
                    </div>
                    <div class="priority-option priority-medium selected" data-priority="medium">
                        <span class="priority-indicator"></span>
                        Medium
                    </div>
                    <div class="priority-option priority-low" data-priority="low">
                        <span class="priority-indicator"></span>
                        Low
                    </div>
                </div>
                
                <label>Category</label>
                <select id="orgSelect">
                    <option value="">Select category...</option>
                    <option value="at">Auckland Transport</option>
                    <option value="ac">Auckland Council</option>
                    <option value="integrated">Integrated/Joint</option>
                    <option value="commercial">Commercial</option>
                    <option value="personal">Personal</option>
                </select>
                
                <div id="dueDateGroup" style="display:none">
                    <label>Target Date</label>
                    <input type="date" id="dueDateInput">
                </div>
                
                <div class="links-section">
                    <label>Links:</label>
                    <div class="link-input-group">
                        <input type="text" id="linkNameInput" placeholder="Link name/label (optional)" style="flex: 0.4;">
                        <input type="url" id="linkInput" placeholder="Add URL">
                        <button class="add-link-btn" onclick="addLink()">+</button>
                    </div>
                    <div class="links-list" id="linksList"></div>
                </div>
                
                <input type="url" id="googleDriveInput" placeholder="Google Drive folder URL (optional)">
                
                <div class="file-upload-section">
                    <div class="file-upload-label">
                        📎 Upload Documents
                    </div>
                    <label for="fileInput" class="file-upload-btn">
                        Choose Files
                    </label>
                    <span class="file-count" id="fileCount">no files selected</span>
                    <input type="file" id="fileInput" multiple accept=".pdf,.doc,.docx,.txt,.xlsx,.pptx,.jpg,.png,.html,.htm" style="display: none;">
                    <div id="filePreview" style="margin-top: 16px;"></div>
                </div>
                
                <div class="modal-actions">
                    <button class="btn" onclick="closeModal()">Cancel</button>
                    <button class="btn btn-primary" onclick="saveItem()">Save</button>
                </div>
            </div>
        </div>

        <!-- HTML Paste Modal -->
        <div class="overlay" id="htmlPasteOverlay">
            <div class="html-paste-modal">
                <h3>Add HTML Content</h3>
                <input type="text" id="htmlTitle" placeholder="Enter a title for this HTML content" required>
                <textarea id="htmlContent" placeholder="Paste your HTML code here..." required></textarea>
                <div style="display:flex;gap:10px;justify-content:flex-end">
                    <button class="btn" onclick="closeHtmlPaste()">Cancel</button>
                    <button class="btn" style="background:#2563eb;color:#fff" onclick="saveHtmlContent()">Save</button>
                </div>
            </div>
        </div>

        <!-- Vault Modal -->
        <div class="overlay" id="vaultOverlay">
            <div class="vault-modal">
                <div class="vault-header">
                    <h2>📂 Document Vault</h2>
                    <div style="display: flex; gap: 10px; align-items: center;">
                        <button class="btn" onclick="configureObsidian()" style="background: #7c3aed;">⚙️ Obsidian Settings</button>
                        <button class="vault-close" onclick="closeVault()">×</button>
                    </div>
                </div>
                
                <div class="category-bar">
                    <div class="category-tabs" id="categoryTabs">
                        <!-- Categories will be rendered here -->
                    </div>
                    <button class="add-category-btn" onclick="showCategoryModal()">
                        + Add Category
                    </button>
                </div>
                
                <div class="vault-controls">
                    <div class="vault-search">
                        <input type="text" id="vaultSearch" placeholder="Search documents..." onkeyup="searchVault()">
                    </div>
                    <div class="vault-filters">
                        <select id="vaultFilter" onchange="filterVault()">
                            <option value="all">All Documents</option>
                            <option value="pdf">PDF Files</option>
                            <option value="doc">Word Documents</option>
                            <option value="xls">Spreadsheets</option>
                            <option value="img">Images</option>
                            <option value="html">HTML Files</option>
                            <option value="other">Other</option>
                        </select>
                        <select id="vaultSort" onchange="sortVault()">
                            <option value="date-desc">Newest First</option>
                            <option value="date-asc">Oldest First</option>
                            <option value="name-asc">Name (A-Z)</option>
                            <option value="name-desc">Name (Z-A)</option>
                        </select>
                    </div>
                </div>
                
                <div class="vault-stats">
                    <div class="vault-stat">
                        <span class="vault-stat-value" id="vaultTotal">0</span>
                        <span class="vault-stat-label">Total Files</span>
                    </div>
                    <div class="vault-stat">
                        <span class="vault-stat-value" id="vaultSize">0 MB</span>
                        <span class="vault-stat-label">Total Size</span>
                    </div>
                    <div class="vault-stat">
                        <span class="vault-stat-value" id="vaultRecent">0</span>
                        <span class="vault-stat-label">Added This Week</span>
                    </div>
                    <div class="vault-stat">
                        <span class="vault-stat-value" id="categoryCount">0</span>
                        <span class="vault-stat-label">In Category</span>
                    </div>
                </div>
                
                <div class="vault-content" id="vaultContent">
                    <div class="vault-empty">
                        <div class="vault-empty-icon">📂</div>
                        <p>No files in vault yet</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Category Modal -->
        <div class="overlay" id="categoryModalOverlay">
            <div class="category-modal">
                <h3>Add New Category</h3>
                <input type="text" id="categoryName" placeholder="Category name" required>
                
                <label>Category Color</label>
                <div class="color-picker">
                    <div class="color-option" data-color="#FF6B6B" style="background: #FF6B6B"></div>
                    <div class="color-option" data-color="#4ECDC4" style="background: #4ECDC4"></div>
                    <div class="color-option" data-color="#45B7D1" style="background: #45B7D1"></div>
                    <div class="color-option" data-color="#FFA07A" style="background: #FFA07A"></div>
                    <div class="color-option" data-color="#98D8C8" style="background: #98D8C8"></div>
                    <div class="color-option" data-color="#FDCB6E" style="background: #FDCB6E"></div>
                    <div class="color-option" data-color="#6C5CE7" style="background: #6C5CE7"></div>
                    <div class="color-option" data-color="#A8E6CF" style="background: #A8E6CF"></div>
                    <div class="color-option selected" data-color="#0066CC" style="background: #0066CC"></div>
                </div>
                
                <div style="display:flex;gap:10px;justify-content:flex-end;margin-top:20px">
                    <button class="btn" onclick="closeCategoryModal()">Cancel</button>
                    <button class="btn" style="background:#2563eb;color:#fff" onclick="saveCategory()">Save</button>
                </div>
            </div>
        </div>

        <!-- File Preview Modal -->
        <div class="overlay" id="previewOverlay">
            <div class="modal">
                <h3 id="previewTitle">Document Preview</h3>
                <div id="previewContent"></div>
                <button class="btn" style="margin-top:20px" onclick="closePreview()">Close</button>
            </div>
        </div>

        <!-- Notification -->
        <div class="notification" id="notification"></div>
    </div>

    <script>
        // Global data
        let data = {
            overview: [],
            workstreams: [],
            projects: [],
            commercial: [],
            vault: [],
            categories: [
                { id: 'cat-1', name: 'Project Documents', color: '#0066CC' },
                { id: 'cat-2', name: 'Pacific Energy', color: '#FDCB6E' },
                { id: 'cat-3', name: 'fixauckland Campaign', color: '#dc2626' }
            ],
            htmlDisplays: [],
            obsidianVault: '' // Store Obsidian vault name
        };

        let currentTab = 'overview';
        let editId = null;
        let selectedPriority = 'medium';
        let tempFiles = [];
        let tempLinks = [];
        let selectedCategory = 'all';
        let vaultSearch = '';
        let vaultFilter = 'all';
        let vaultSort = 'date-desc';

        // Initialize
        function init() {
            loadData();
            setupEventListeners();
            switchTab('overview');
            updateStats();
            updateVaultBadge();
        }

        // Setup event listeners
        function setupEventListeners() {
            // Tab navigation
            document.querySelectorAll('.tab').forEach(tab => {
                tab.addEventListener('click', () => {
                    switchTab(tab.dataset.type);
                });
            });
            
            // Priority selector
            document.querySelectorAll('.priority-option').forEach(opt => {
                opt.addEventListener('click', (e) => {
                    e.preventDefault();
                    document.querySelectorAll('.priority-option').forEach(o => o.classList.remove('selected'));
                    opt.classList.add('selected');
                    selectedPriority = opt.dataset.priority;
                });
            });
            
            // File input
            document.getElementById('fileInput').addEventListener('change', (event) => {
                handleFileSelect(event);
                updateFileCount();
            });
            
            // Color picker for categories
            document.querySelectorAll('.color-option').forEach(opt => {
                opt.addEventListener('click', () => {
                    document.querySelectorAll('.color-option').forEach(o => o.classList.remove('selected'));
                    opt.classList.add('selected');
                });
            });
        }

        // Switch tabs
        function switchTab(type) {
            currentTab = type;
            document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
            document.querySelector(`[data-type="${type}"]`).classList.add('active');
            renderContent();
        }

        // Render content
        function renderContent() {
            const main = document.getElementById('mainContent');
            let html = '<div class="panel active">';
            
            if (currentTab === 'overview') {
                html += renderOverview();
            } else {
                html += `
                    <div class="panel-header">
                        <h2>${getTabTitle(currentTab)}</h2>
                        <button class="add-btn" onclick="openModal()">+ Add ${getSingularType(currentTab)}</button>
                    </div>
                    <div class="grid">
                `;
                
                data[currentTab].forEach(item => {
                    html += renderCard(item, currentTab);
                });
                
                html += '</div>';
            }
            
            html += '</div>';
            main.innerHTML = html;
            
            // Display first HTML if on overview
            if (currentTab === 'overview' && data.htmlDisplays.length > 0) {
                setTimeout(() => displayHtmlContent(0), 100);
            }
        }

        // Render overview
        function renderOverview() {
            const highPriority = data.projects.filter(p => p.priority === 'high');
            const activeWorkstreams = data.workstreams.filter(w => w.priority === 'high' || w.priority === 'medium');
            
            let html = `
                <div class="quick-actions">
                    <button class="quick-action-btn" onclick="switchTab('projects'); openModal()">➕ New Project</button>
                    <button class="quick-action-btn" onclick="switchTab('workstreams'); openModal()">➕ New Workstream</button>
                    <button class="quick-action-btn secondary" onclick="openVault()">📂 Open Vault</button>
                </div>
                
                <div class="overview-content">
                    <div class="overview-section">
                        <h3 data-count="${highPriority.length}">🔥 High Priority Projects</h3>
                        <div class="overview-items">
            `;
            
            if (highPriority.length === 0) {
                html += '<div class="overview-empty">No high priority projects</div>';
            } else {
                highPriority.forEach(p => {
                    html += `
                        <div class="overview-item" onclick="switchTab('projects')">
                            <div class="overview-item-icon">${getPriorityIcon(p.priority)}</div>
                            <div class="overview-item-content">
                                <strong>${escapeHtml(p.title)}</strong>
                                <div class="overview-item-meta">
                                    ${p.organization ? `<span>${getOrgShortName(p.organization)}</span>` : ''}
                                    ${p.dueDate ? `<span>Due: ${new Date(p.dueDate).toLocaleDateString()}</span>` : ''}
                                </div>
                            </div>
                        </div>
                    `;
                });
            }
            
            html += `
                        </div>
                    </div>
                    
                    <div class="overview-section">
                        <h3 data-count="${activeWorkstreams.length}">🔄 Active Workstreams</h3>
                        <div class="overview-items">
            `;
            
            if (activeWorkstreams.length === 0) {
                html += '<div class="overview-empty">No active workstreams</div>';
            } else {
                activeWorkstreams.forEach(w => {
                    html += `
                        <div class="overview-item" onclick="switchTab('workstreams')">
                            <div class="overview-item-icon">${getPriorityIcon(w.priority)}</div>
                            <div class="overview-item-content">
                                <strong>${escapeHtml(w.title)}</strong>
                                <div class="overview-item-meta">
                                    <span>${w.priority} priority</span>
                                    ${w.organization ? `<span>${getOrgShortName(w.organization)}</span>` : ''}
                                </div>
                            </div>
                        </div>
                    `;
                });
            }
            
            html += `
                        </div>
                    </div>
                    
                    <div class="overview-section">
                        <h3 data-count="${data.htmlDisplays.length}">🌐 HTML Displays</h3>
                        <div class="overview-items">
            `;
            
            if (data.htmlDisplays.length === 0) {
                html += '<div class="overview-empty">No HTML content yet</div>';
            } else {
                data.htmlDisplays.forEach((item, index) => {
                    html += `
                        <div class="overview-item" style="cursor: default;">
                            <div style="display: flex; align-items: center; gap: 12px; width: 100%;">
                                <div class="overview-item-icon" onclick="displayHtmlContent(${index})" style="cursor: pointer;">🌐</div>
                                <div class="overview-item-content" onclick="displayHtmlContent(${index})" style="cursor: pointer; flex: 1;">
                                    <strong>${escapeHtml(item.title)}</strong>
                                    <div class="overview-item-meta">
                                        <span>${new Date(item.createdAt).toLocaleDateString()}</span>
                                    </div>
                                </div>
                                <button class="pill red" onclick="deleteHtmlDisplay(${index}, event)" style="font-size: 0.75rem; padding: 4px 10px;">Delete</button>
                            </div>
                        </div>
                    `;
                });
            }
            
            html += `
                            <button class="add-btn" style="margin-top: 12px; width: 100%;" onclick="openHtmlPaste()">+ Add HTML</button>
                        </div>
                    </div>
                </div>
                
                <div class="html-display-area" id="htmlDisplayArea">
            `;
            
            if (data.htmlDisplays.length > 0) {
                html += `
                    <div class="html-display-header">
                        <h3 id="htmlDisplayTitle">${escapeHtml(data.htmlDisplays[0].title)}</h3>
                        <div class="html-display-controls">
                            <button class="html-control-btn" onclick="openHtmlFullscreen(0)">⛶ Fullscreen</button>
                        </div>
                    </div>
                    <iframe class="html-content-frame" id="htmlDisplayFrame"></iframe>
                `;
            } else {
                html += `
                    <div class="html-empty-state">
                        <div class="html-empty-icon">📄</div>
                        <p>Select an HTML display from the list above to view it here</p>
                    </div>
                `;
            }
            
            html += '</div>';
            
            return html;
        }

        // Render card
        function renderCard(item, type) {
            const orgTag = item.organization ? `<span class="status-tag tag-${item.organization}">${getOrgName(item.organization)}</span>` : '';
            
            let html = `
                <div class="card">
                    ${item.priority ? `<span class="priority-badge priority-${item.priority}">${item.priority.toUpperCase()}</span>` : ''}
                    <button class="del" onclick="deleteItem('${item.id}', '${type}')">×</button>
                    <h3>${escapeHtml(item.title)}</h3>
                    <p>${escapeHtml(item.description || '')}</p>
                    
                    ${orgTag ? `<div class="status-tags">${orgTag}</div>` : ''}
                    
                    ${type === 'projects' && item.dueDate ? 
                        `<p><small>Target: ${new Date(item.dueDate).toLocaleDateString()}</small></p>` : ''
                    }
                    
                    ${item.googleDriveUrl ? 
                        `<p><a href="${item.googleDriveUrl}" target="_blank" style="color:#60a5fa">📁 Google Drive</a></p>` : ''
                    }
                    
                    ${renderLinks(item.links)}
                    
                    ${item.link && (!item.links || item.links.length === 0) ? 
                        `<p><a href="${item.link}" target="_blank" style="color:#60a5fa">View Link</a></p>` : ''
                    }
            `;
            
            // Add file list if files exist
            if (item.files && item.files.length > 0) {
                html += '<div class="file-list">';
                item.files.forEach(file => {
                    html += `
                        <div class="file-item">
                            <div class="file-info">
                                <span>${getFileIcon(file.name)}</span>
                                <span>${file.name}</span>
                            </div>
                            <div class="file-actions">
                                <span class="vault-status">${isFileInVault(file.id) ? 'In Vault' : 'Local Only'}</span>
                                <button class="pill blue" onclick="viewFile('${file.id}', event)">👁️ View</button>
                                ${!isFileInVault(file.id) ? `<button class="pill green" onclick="addToVault('${file.id}', '${type}', '${item.id}', event)">+ Vault</button>` : ''}
                            </div>
                        </div>
                    `;
                });
                html += '</div>';
            }
            
            html += `
                    <div class="actions">
                        <button class="pill blue" onclick="editItem('${item.id}', '${type}')">Edit</button>
                        <button class="pill purple" onclick="sendToObsidian('${item.id}', '${type}')">📝 Obsidian</button>
                    </div>
                </div>
            `;
            
            return html;
        }

        // Display HTML content
        function displayHtmlContent(index) {
            const item = data.htmlDisplays[index];
            if (!item) return;
            
            const displayArea = document.getElementById('htmlDisplayArea');
            if (!displayArea) return;
            
            displayArea.innerHTML = `
                <div class="html-display-header">
                    <h3 id="htmlDisplayTitle">${escapeHtml(item.title)}</h3>
                    <div class="html-display-controls">
                        <button class="html-control-btn" onclick="openHtmlFullscreen(${index})">⛶ Fullscreen</button>
                    </div>
                </div>
                <iframe class="html-content-frame" id="htmlDisplayFrame"></iframe>
            `;
            
            setTimeout(() => {
                const iframe = document.getElementById('htmlDisplayFrame');
                if (iframe) {
                    iframe.srcdoc = item.content;
                }
            }, 50);
        }

        // Open modal
        function openModal() {
            editId = null;
            selectedPriority = 'medium';
            tempFiles = [];
            tempLinks = [];
            
            document.getElementById('modalTitle').textContent = `Edit ${getSingularType(currentTab)}`;
            document.getElementById('titleInput').value = '';
            document.getElementById('descInput').value = '';
            document.getElementById('linkInput').value = '';
            document.getElementById('linkNameInput').value = '';
            document.getElementById('orgSelect').value = '';
            document.getElementById('dueDateInput').value = '';
            document.getElementById('googleDriveInput').value = '';
            document.getElementById('fileInput').value = '';
            document.getElementById('filePreview').innerHTML = '';
            document.getElementById('linksList').innerHTML = '';
            updateFileCount();
            
            // Reset priority buttons
            document.querySelectorAll('.priority-option').forEach(o => o.classList.remove('selected'));
            document.querySelector('[data-priority="medium"]').classList.add('selected');
            
            // Show/hide date field
            document.getElementById('dueDateGroup').style.display = 
                currentTab === 'projects' ? 'block' : 'none';
            
            document.getElementById('modalOverlay').classList.add('show');
        }

        // Close modal
        function closeModal() {
            document.getElementById('modalOverlay').classList.remove('show');
            tempFiles = [];
            tempLinks = [];
        }

        // Edit item
        function editItem(id, type) {
            const item = data[type].find(i => i.id === id);
            if (!item) return;
            
            editId = id;
            selectedPriority = item.priority || 'medium';
            tempFiles = item.files || [];
            tempLinks = item.links || [];
            
            // For backward compatibility, if item has old 'link' field but no 'links' array
            if (!tempLinks.length && item.link) {
                tempLinks = [{
                    id: generateId(),
                    name: item.link,
                    url: item.link
                }];
            }
            
            document.getElementById('modalTitle').textContent = `Edit ${getSingularType(type)}`;
            document.getElementById('titleInput').value = item.title;
            document.getElementById('descInput').value = item.description || '';
            document.getElementById('orgSelect').value = item.organization || '';
            document.getElementById('dueDateInput').value = item.dueDate || '';
            document.getElementById('googleDriveInput').value = item.googleDriveUrl || '';
            
            // Clear single link input fields
            document.getElementById('linkInput').value = '';
            document.getElementById('linkNameInput').value = '';
            
            // Set priority
            document.querySelectorAll('.priority-option').forEach(o => o.classList.remove('selected'));
            const priorityBtn = document.querySelector(`[data-priority="${item.priority || 'medium'}"]`);
            if (priorityBtn) priorityBtn.classList.add('selected');
            
            // Update file preview and links
            updateFilePreview();
            updateLinksList();
            updateFileCount();
            
            // Show/hide date field
            document.getElementById('dueDateGroup').style.display = 
                type === 'projects' ? 'block' : 'none';
            
            document.getElementById('modalOverlay').classList.add('show');
        }

        // Save item
        function saveItem() {
            const title = document.getElementById('titleInput').value.trim();
            if (!title) {
                showNotification('Please enter a title', 'error');
                return;
            }
            
            const item = {
                id: editId || generateId(),
                title,
                description: document.getElementById('descInput').value.trim(),
                priority: selectedPriority,
                organization: document.getElementById('orgSelect').value,
                links: [...tempLinks],
                googleDriveUrl: document.getElementById('googleDriveInput').value.trim(),
                files: [...tempFiles],
                createdAt: new Date().toISOString()
            };
            
            // Maintain backward compatibility - add first link as main link
            if (tempLinks.length > 0) {
                item.link = tempLinks[0].url;
            }
            
            if (currentTab === 'projects') {
                item.dueDate = document.getElementById('dueDateInput').value;
            }
            
            if (editId) {
                // Update existing - preserve createdAt date
                const index = data[currentTab].findIndex(i => i.id === editId);
                if (index !== -1) {
                    const existingItem = data[currentTab][index];
                    item.createdAt = existingItem.createdAt || item.createdAt;
                    data[currentTab][index] = item;
                }
            } else {
                // Add new
                data[currentTab].unshift(item);
            }
            
            saveData();
            renderContent();
            updateStats();
            closeModal();
            showNotification(`${getSingularType(currentTab)} ${editId ? 'updated' : 'added'} successfully`);
        }

        // Delete item
        function deleteItem(id, type) {
            if (confirm('Are you sure you want to delete this item?')) {
                data[type] = data[type].filter(i => i.id !== id);
                saveData();
                renderContent();
                updateStats();
                showNotification('Item deleted successfully');
            }
        }

        // Delete HTML Display
        function deleteHtmlDisplay(index, event) {
            if (event) event.stopPropagation();
            
            if (confirm('Delete this HTML display? This will also remove it from the vault if it exists there.')) {
                const htmlItem = data.htmlDisplays[index];
                
                // Remove from htmlDisplays
                data.htmlDisplays.splice(index, 1);
                
                // Also remove from vault if it exists
                const vaultFileName = htmlItem.title + '.html';
                data.vault = data.vault.filter(f => f.name !== vaultFileName || f.sourceType !== 'htmlDisplay');
                
                saveData();
                renderContent();
                updateVaultBadge();
                showNotification('HTML display deleted');
            }
        }

        // Link management functions
        function addLink() {
            const url = document.getElementById('linkInput').value.trim();
            const name = document.getElementById('linkNameInput').value.trim();
            
            if (!url) {
                showNotification('Please enter a URL', 'error');
                return;
            }
            
            tempLinks.push({
                id: generateId(),
                name: name || url,
                url: url
            });
            
            document.getElementById('linkInput').value = '';
            document.getElementById('linkNameInput').value = '';
            updateLinksList();
        }

        function updateLinksList() {
            const linksList = document.getElementById('linksList');
            if (tempLinks.length === 0) {
                linksList.innerHTML = '';
                return;
            }
            
            let html = '';
            tempLinks.forEach((link, index) => {
                html += `
                    <div class="link-item">
                        <span>${escapeHtml(link.name)}</span>
                        <button onclick="removeTempLink(${index})">×</button>
                    </div>
                `;
            });
            linksList.innerHTML = html;
        }

        function removeTempLink(index) {
            tempLinks.splice(index, 1);
            updateLinksList();
        }

        function renderLinks(links) {
            if (!links || links.length === 0) return '';
            
            let html = '<div style="margin-top: 8px;">';
            links.forEach(link => {
                html += `<p><a href="${link.url}" target="_blank" style="color:#60a5fa">${escapeHtml(link.name)}</a></p>`;
            });
            html += '</div>';
            return html;
        }

        // File handling functions
        function updateFileCount() {
            const count = tempFiles.length;
            const fileCount = document.getElementById('fileCount');
            if (fileCount) {
                fileCount.textContent = count === 0 ? 'no files selected' : 
                                       count === 1 ? '1 file selected' : 
                                       `${count} files selected`;
            }
        }

        function handleFileSelect(event) {
            const files = Array.from(event.target.files);
            
            files.forEach(file => {
                const reader = new FileReader();
                reader.onload = (e) => {
                    const fileData = {
                        id: generateId(),
                        name: file.name,
                        size: file.size,
                        type: file.type,
                        data: e.target.result,
                        uploadedAt: new Date().toISOString()
                    };
                    tempFiles.push(fileData);
                    updateFilePreview();
                };
                reader.readAsDataURL(file);
            });
        }

        function updateFilePreview() {
            const preview = document.getElementById('filePreview');
            if (tempFiles.length === 0) {
                preview.innerHTML = '';
                return;
            }
            
            let html = '<div style="margin-top:10px">';
            tempFiles.forEach((file, index) => {
                html += `
                    <div class="link-item">
                        <span>${getFileIcon(file.name)} ${file.name}</span>
                        <button onclick="removeTempFile(${index})">×</button>
                    </div>
                `;
            });
            html += '</div>';
            preview.innerHTML = html;
        }

        function removeTempFile(index) {
            tempFiles.splice(index, 1);
            updateFilePreview();
            updateFileCount();
        }

        function viewFile(fileId, event) {
            if (event) event.stopPropagation();
            
            // Find file in all data
            let file = null;
            for (const type of ['projects', 'workstreams', 'commercial']) {
                for (const item of data[type]) {
                    if (item.files) {
                        const found = item.files.find(f => f.id === fileId);
                        if (found) {
                            file = found;
                            break;
                        }
                    }
                }
                if (file) break;
            }
            
            if (!file) {
                const vaultFile = data.vault.find(f => f.id === fileId);
                if (vaultFile) file = vaultFile;
            }
            
            if (!file) {
                showNotification('File not found', 'error');
                return;
            }
            
            // Validate file data
            if (!file.data || !file.data.startsWith('data:')) {
                showNotification('File data is corrupted', 'error');
                return;
            }
            
            // Always use the preview modal for viewing files
            openFileViewer(file);
        }

        function openFileViewer(file) {
            const overlay = document.getElementById('previewOverlay');
            const title = document.getElementById('previewTitle');
            const content = document.getElementById('previewContent');
            
            title.textContent = file.name;
            
            const ext = file.name.split('.').pop().toLowerCase();
            
            // Handle different file types
            if (['jpg', 'jpeg', 'png', 'gif', 'svg', 'webp'].includes(ext)) {
                // Images
                content.innerHTML = `
                    <div style="text-align: center;">
                        <img src="${file.data}" style="max-width:100%;max-height:70vh;height:auto;">
                    </div>
                `;
            } else if (['pdf'].includes(ext)) {
                // PDFs
                content.innerHTML = `
                    <iframe src="${file.data}" style="width:100%;height:70vh;border:1px solid #2d3f57;border-radius:8px;"></iframe>
                    <div style="margin-top:10px;">
                        <button class="btn" onclick="window.open('${file.data}', '_blank')">Open in New Tab</button>
                    </div>
                `;
            } else if (['html', 'htm'].includes(ext)) {
                // HTML files
                content.innerHTML = `
                    <iframe id="htmlViewFrame" style="width:100%;height:70vh;border:1px solid #2d3f57;border-radius:8px;background:#fff;"></iframe>
                    <div style="margin-top:10px;">
                        <button class="btn" onclick="openHtmlInNewWindow('${file.id}')">Open in New Window</button>
                    </div>
                `;
                // Set HTML content after DOM update
                setTimeout(() => {
                    const iframe = document.getElementById('htmlViewFrame');
                    if (iframe) {
                        try {
                            if (file.data.startsWith('data:text/html')) {
                                const content = atob(file.data.split(',')[1]);
                                iframe.srcdoc = content;
                            } else {
                                iframe.src = file.data;
                            }
                        } catch (e) {
                            iframe.srcdoc = '<p>Error loading HTML content</p>';
                        }
                    }
                }, 50);
            } else if (['txt', 'md', 'json', 'xml', 'csv', 'log'].includes(ext)) {
                // Text files
                try {
                    const base64Content = file.data.split(',')[1];
                    const textContent = atob(base64Content);
                    content.innerHTML = `
                        <pre style="white-space: pre-wrap; word-wrap: break-word; max-height: 70vh; overflow-y: auto; padding: 20px; background: #0f1419; border-radius: 8px; border: 1px solid #2d3f57;">${escapeHtml(textContent)}</pre>
                    `;
                } catch (e) {
                    content.innerHTML = '<p>Unable to preview this text file</p>';
                }
            } else if (['doc', 'docx', 'xls', 'xlsx', 'ppt', 'pptx'].includes(ext)) {
                // Office files
                content.innerHTML = `
                    <div style="text-align:center;padding:40px;">
                        <div style="font-size:4rem;opacity:0.5;margin-bottom:20px;">${getFileIcon(file.name)}</div>
                        <p>Preview not available for ${ext.toUpperCase()} files</p>
                        <div style="margin-top:20px;">
                            <button class="btn" onclick="downloadFile('${file.id}', event)">Download to View</button>
                        </div>
                    </div>
                `;
            } else {
                // Other files
                content.innerHTML = `
                    <div style="text-align:center;padding:40px;">
                        <div style="font-size:4rem;opacity:0.5;margin-bottom:20px;">📎</div>
                        <p>Preview not available for this file type</p>
                        <p style="color:#94a3b8;font-size:0.9rem;">File: ${file.name}</p>
                        <div style="margin-top:20px;">
                            <button class="btn" onclick="downloadFile('${file.id}', event)">Download File</button>
                        </div>
                    </div>
                `;
            }
            
            overlay.classList.add('show');
        }

        function openHtmlInNewWindow(fileId) {
            const file = data.vault.find(f => f.id === fileId) || 
                         data.projects.concat(data.workstreams, data.commercial)
                             .flatMap(item => item.files || [])
                             .find(f => f.id === fileId);
            
            if (!file) return;
            
            const newWindow = window.open('', '_blank');
            if (file.data.startsWith('data:text/html')) {
                const content = atob(file.data.split(',')[1]);
                newWindow.document.write(content);
            } else {
                newWindow.document.write(`
                    <!DOCTYPE html>
                    <html>
                    <head>
                        <title>${file.name}</title>
                        <style>
                            body { margin: 0; padding: 0; }
                            iframe { width: 100vw; height: 100vh; border: none; }
                        </style>
                    </head>
                    <body>
                        <iframe src="${file.data}"></iframe>
                    </body>
                    </html>
                `);
            }
            newWindow.document.close();
        }

        function closePreview() {
            document.getElementById('previewOverlay').classList.remove('show');
        }

        function addToVault(fileId, type, itemId, event) {
            if (event) event.stopPropagation();
            
            // Find the file
            const item = data[type].find(i => i.id === itemId);
            if (!item || !item.files) return;
            
            const file = item.files.find(f => f.id === fileId);
            if (!file) return;
            
            // Add to vault with metadata
            const vaultFile = {
                ...file,
                category: data.categories[0]?.id || 'uncategorized',
                sourceType: type,
                sourceItemId: itemId,
                addedToVault: new Date().toISOString()
            };
            
            data.vault.push(vaultFile);
            saveData();
            updateVaultBadge();
            showNotification('File added to vault');
            
            // Refresh the current view
            renderContent();
        }

        function isFileInVault(fileId) {
            return data.vault.some(f => f.id === fileId);
        }

        // HTML Display methods
        function openHtmlPaste() {
            document.getElementById('htmlTitle').value = '';
            document.getElementById('htmlContent').value = '';
            document.getElementById('htmlPasteOverlay').classList.add('show');
        }

        function closeHtmlPaste() {
            document.getElementById('htmlPasteOverlay').classList.remove('show');
        }

        function saveHtmlContent() {
            const title = document.getElementById('htmlTitle').value.trim();
            const content = document.getElementById('htmlContent').value.trim();
            
            if (!title || !content) {
                showNotification('Please enter both title and HTML content', 'error');
                return;
            }
            
            const htmlItem = {
                id: generateId(),
                title,
                content,
                createdAt: new Date().toISOString()
            };
            
            data.htmlDisplays.push(htmlItem);
            
            // Also add to vault automatically
            const htmlFile = {
                id: generateId(),
                name: title + '.html',
                size: new Blob([content]).size,
                type: 'text/html',
                data: 'data:text/html;base64,' + btoa(content),
                uploadedAt: new Date().toISOString(),
                category: data.categories[0]?.id || 'uncategorized',
                sourceType: 'htmlDisplay',
                addedToVault: new Date().toISOString()
            };
            
            data.vault.push(htmlFile);
            
            saveData();
            closeHtmlPaste();
            renderContent();
            updateVaultBadge();
            showNotification('HTML content added successfully and saved to vault');
        }

        function openHtmlFullscreen(index) {
            const item = data.htmlDisplays[index];
            if (!item) return;
            
            const fullscreenHtml = `
                <!DOCTYPE html>
                <html>
                <head>
                    <title>${escapeHtml(item.title)}</title>
                    <style>
                        body { margin: 0; padding: 0; }
                        .header { 
                            background: #0f1419; 
                            color: white; 
                            padding: 10px 20px; 
                            display: flex; 
                            justify-content: space-between; 
                            align-items: center;
                        }
                        .content { height: calc(100vh - 50px); }
                        button { 
                            background: #dc2626; 
                            color: white; 
                            border: none; 
                            padding: 8px 16px; 
                            border-radius: 6px; 
                            cursor: pointer;
                        }
                    </style>
                </head>
                <body>
                    <div class="header">
                        <h3>${escapeHtml(item.title)}</h3>
                        <button onclick="window.close()">Close</button>
                    </div>
                    <div class="content">${item.content}</div>
                </body>
                </html>
            `;
            
            const win = window.open('', '_blank');
            win.document.write(fullscreenHtml);
            win.document.close();
        }

        // Send to Obsidian
        function sendToObsidian(id, type) {
            const item = data[type].find(i => i.id === id);
            if (!item) return;
            
            // Check if Obsidian vault is configured
            if (!data.obsidianVault) {
                const vaultName = prompt('Please enter your Obsidian vault name:', 'MyVault');
                if (!vaultName) return;
                data.obsidianVault = vaultName;
                saveData();
            }
            
            // Format content for Obsidian
            let obsidianContent = `# ${item.title}\n\n`;
            obsidianContent += `**Type:** ${getSingularType(type)}\n`;
            obsidianContent += `**Priority:** ${item.priority || 'Not set'}\n`;
            obsidianContent += `**Organization:** ${item.organization ? getOrgName(item.organization) : 'Not set'}\n`;
            obsidianContent += `**Created:** ${new Date(item.createdAt).toLocaleDateString()}\n`;
            
            if (type === 'projects' && item.dueDate) {
                obsidianContent += `**Due Date:** ${new Date(item.dueDate).toLocaleDateString()}\n`;
            }
            
            obsidianContent += `\n## Description\n${item.description || 'No description provided'}\n`;
            
            if (item.googleDriveUrl) {
                obsidianContent += `\n## Google Drive\n[Open Google Drive Folder](${item.googleDriveUrl})\n`;
            }
            
            if (item.links && item.links.length > 0) {
                obsidianContent += `\n## Links\n`;
                item.links.forEach(link => {
                    obsidianContent += `- [${link.name}](${link.url})\n`;
                });
            }
            
            if (item.files && item.files.length > 0) {
                obsidianContent += `\n## Attached Files\n`;
                item.files.forEach(file => {
                    obsidianContent += `- ${file.name}\n`;
                });
            }
            
            obsidianContent += `\n---\n*Exported from Myworkspace on ${new Date().toLocaleString()}*`;
            
            // Create Obsidian URI
            const encodedContent = encodeURIComponent(obsidianContent);
            const encodedTitle = encodeURIComponent(item.title);
            const obsidianUri = `obsidian://new?vault=${encodeURIComponent(data.obsidianVault)}&name=${encodedTitle}&content=${encodedContent}`;
            
            // Try to open in Obsidian
            window.open(obsidianUri, '_blank');
            
            showNotification('Sent to Obsidian! Check your Obsidian app.');
        }

        // Configure Obsidian
        function configureObsidian() {
            const currentVault = data.obsidianVault || 'Not configured';
            const newVault = prompt(`Enter your Obsidian vault name:\n\nCurrent vault: ${currentVault}`, data.obsidianVault || '');
            
            if (newVault !== null && newVault.trim() !== '') {
                data.obsidianVault = newVault.trim();
                saveData();
                showNotification('Obsidian vault configured successfully');
            }
        }

        // Send file to Obsidian
        function sendFileToObsidian(fileId, event) {
            if (event) event.stopPropagation();
            
            // Check if Obsidian vault is configured
            if (!data.obsidianVault) {
                const vaultName = prompt('Please enter your Obsidian vault name:', 'MyVault');
                if (!vaultName) return;
                data.obsidianVault = vaultName;
                saveData();
            }
            
            const file = data.vault.find(f => f.id === fileId);
            if (!file) return;
            
            // Create a note with file information
            let obsidianContent = `# ${file.name}\n\n`;
            obsidianContent += `**Type:** ${file.type || 'Unknown'}\n`;
            obsidianContent += `**Size:** ${formatFileSize(file.size)}\n`;
            obsidianContent += `**Added to Vault:** ${new Date(file.addedToVault || file.uploadedAt).toLocaleDateString()}\n`;
            
            if (file.category && file.category !== 'uncategorized') {
                obsidianContent += `**Category:** ${getCategoryName(file.category)}\n`;
            }
            
            obsidianContent += `\n## File Information\n`;
            obsidianContent += `This file was imported from Myworkspace Document Vault.\n`;
            
            // For text-based files, try to include content
            const ext = file.name.split('.').pop().toLowerCase();
            if (['txt', 'md'].includes(ext)) {
                try {
                    const base64Content = file.data.split(',')[1];
                    const textContent = atob(base64Content);
                    obsidianContent += `\n## Content\n\`\`\`\n${textContent}\n\`\`\`\n`;
                } catch (e) {
                    obsidianContent += `\n*Content could not be extracted*\n`;
                }
            }
            
            obsidianContent += `\n---\n*Imported from Myworkspace on ${new Date().toLocaleString()}*`;
            
            // Create Obsidian URI
            const encodedContent = encodeURIComponent(obsidianContent);
            const encodedTitle = encodeURIComponent(file.name.replace(/\.[^/.]+$/, '')); // Remove extension
            const obsidianUri = `obsidian://new?vault=${encodeURIComponent(data.obsidianVault)}&name=${encodedTitle}&content=${encodedContent}`;
            
            // Try to open in Obsidian
            window.open(obsidianUri, '_blank');
            
            showNotification('File information sent to Obsidian!');
        }

        // Vault functions
        function openVault() {
            renderCategories();
            renderVaultContent();
            updateVaultStats();
            document.getElementById('vaultOverlay').classList.add('show');
        }

        function closeVault() {
            document.getElementById('vaultOverlay').classList.remove('show');
        }

        function renderCategories() {
            const tabs = document.getElementById('categoryTabs');
            let html = `
                <div class="category-tab ${selectedCategory === 'all' ? 'active' : ''}" 
                     onclick="selectCategory('all')">
                    All Files
                </div>
            `;
            
            data.categories.forEach(cat => {
                html += `
                    <div class="category-tab ${selectedCategory === cat.id ? 'active' : ''}" 
                         onclick="selectCategory('${cat.id}')">
                        <div class="category-color" style="background:${cat.color}"></div>
                        ${cat.name}
                    </div>
                `;
            });
            
            tabs.innerHTML = html;
        }

        function selectCategory(categoryId) {
            selectedCategory = categoryId;
            renderCategories();
            renderVaultContent();
            updateVaultStats();
        }

        function renderVaultContent() {
            const content = document.getElementById('vaultContent');
            let files = getFilteredVaultFiles();
            
            if (files.length === 0) {
                content.innerHTML = `
                    <div class="vault-empty">
                        <div class="vault-empty-icon">📂</div>
                        <p>No files found</p>
                    </div>
                `;
                return;
            }
            
            let html = '';
            files.forEach(file => {
                html += `
                    <div class="vault-item">
                        <div class="vault-item-icon ${getFileClass(file.name)}">
                            ${getFileIcon(file.name)}
                        </div>
                        <div class="vault-item-info">
                            <div class="vault-item-name">${file.name}</div>
                            <div class="vault-item-meta">
                                <span>${formatFileSize(file.size)}</span>
                                <span>${new Date(file.addedToVault || file.uploadedAt).toLocaleDateString()}</span>
                                ${file.category && file.category !== 'all' ? 
                                    `<span class="vault-item-category">${getCategoryName(file.category)}</span>` : ''
                                }
                            </div>
                        </div>
                        <div class="vault-item-actions">
                            <button class="pill green" onclick="viewFile('${file.id}', event)">👁️ View</button>
                            <button class="pill purple" onclick="sendFileToObsidian('${file.id}', event)">📝 Obsidian</button>
                            <button class="pill blue" onclick="downloadFile('${file.id}', event)">⬇️ Download</button>
                            <button class="pill red" onclick="removeFromVault('${file.id}', event)">❌ Remove</button>
                        </div>
                    </div>
                `;
            });
            
            content.innerHTML = html;
        }

        function getFilteredVaultFiles() {
            let files = [...data.vault];
            
            // Category filter
            if (selectedCategory !== 'all') {
                files = files.filter(f => f.category === selectedCategory);
            }
            
            // Search filter
            if (vaultSearch) {
                const search = vaultSearch.toLowerCase();
                files = files.filter(f => f.name.toLowerCase().includes(search));
            }
            
            // Type filter
            if (vaultFilter !== 'all') {
                files = files.filter(f => {
                    const ext = f.name.split('.').pop().toLowerCase();
                    switch (vaultFilter) {
                        case 'pdf': return ext === 'pdf';
                        case 'doc': return ['doc', 'docx'].includes(ext);
                        case 'xls': return ['xls', 'xlsx'].includes(ext);
                        case 'img': return ['jpg', 'jpeg', 'png', 'gif', 'svg'].includes(ext);
                        case 'html': return ['html', 'htm'].includes(ext);
                        default: return !['pdf', 'doc', 'docx', 'xls', 'xlsx', 'jpg', 'jpeg', 'png', 'gif', 'svg', 'html', 'htm'].includes(ext);
                    }
                });
            }
            
            // Sort
            files.sort((a, b) => {
                switch (vaultSort) {
                    case 'date-asc':
                        return new Date(a.addedToVault || a.uploadedAt) - new Date(b.addedToVault || b.uploadedAt);
                    case 'date-desc':
                        return new Date(b.addedToVault || b.uploadedAt) - new Date(a.addedToVault || a.uploadedAt);
                    case 'name-asc':
                        return a.name.localeCompare(b.name);
                    case 'name-desc':
                        return b.name.localeCompare(a.name);
                    default:
                        return 0;
                }
            });
            
            return files;
        }

        function searchVault() {
            vaultSearch = document.getElementById('vaultSearch').value;
            renderVaultContent();
        }

        function filterVault() {
            vaultFilter = document.getElementById('vaultFilter').value;
            renderVaultContent();
        }

        function sortVault() {
            vaultSort = document.getElementById('vaultSort').value;
            renderVaultContent();
        }

        function updateVaultStats() {
            const files = getFilteredVaultFiles();
            const totalSize = files.reduce((sum, f) => sum + (f.size || 0), 0);
            const weekAgo = new Date();
            weekAgo.setDate(weekAgo.getDate() - 7);
            const recentFiles = files.filter(f => new Date(f.addedToVault || f.uploadedAt) > weekAgo);
            
            document.getElementById('vaultTotal').textContent = files.length;
            document.getElementById('vaultSize').textContent = formatFileSize(totalSize);
            document.getElementById('vaultRecent').textContent = recentFiles.length;
            document.getElementById('categoryCount').textContent = 
                selectedCategory === 'all' ? files.length :
                files.filter(f => f.category === selectedCategory).length;
        }

        function removeFromVault(fileId, event) {
            if (event) event.stopPropagation();
            
            if (confirm('Remove this file from the vault?')) {
                data.vault = data.vault.filter(f => f.id !== fileId);
                saveData();
                updateVaultBadge();
                renderVaultContent();
                updateVaultStats();
                showNotification('File removed from vault');
            }
        }

        function downloadFile(fileId, event) {
            if (event) event.stopPropagation();
            
            const file = data.vault.find(f => f.id === fileId);
            if (!file) return;
            
            const a = document.createElement('a');
            a.href = file.data;
            a.download = file.name;
            a.click();
        }

        // Category management
        function showCategoryModal() {
            document.getElementById('categoryName').value = '';
            document.querySelectorAll('.color-option').forEach(o => o.classList.remove('selected'));
            document.querySelector('[data-color="#0066CC"]').classList.add('selected');
            document.getElementById('categoryModalOverlay').classList.add('show');
        }

        function closeCategoryModal() {
            document.getElementById('categoryModalOverlay').classList.remove('show');
        }

        function saveCategory() {
            const name = document.getElementById('categoryName').value.trim();
            if (!name) {
                showNotification('Please enter a category name', 'error');
                return;
            }
            
            const selectedColor = document.querySelector('.color-option.selected');
            const color = selectedColor ? selectedColor.dataset.color : '#0066CC';
            
            const category = {
                id: generateId(),
                name,
                color
            };
            
            data.categories.push(category);
            saveData();
            renderCategories();
            closeCategoryModal();
            showNotification('Category added successfully');
        }

        function getCategoryName(categoryId) {
            const category = data.categories.find(c => c.id === categoryId);
            return category ? category.name : 'Uncategorized';
        }

        // Utility functions
        function generateId() {
            return 'id-' + Date.now() + '-' + Math.random().toString(36).substr(2, 9);
        }

        function getTabTitle(type) {
            const titles = {
                overview: 'Dashboard Overview',
                workstreams: 'Active Workstreams',
                projects: 'Projects',
                commercial: 'Commercial Activities'
            };
            return titles[type] || type;
        }

        function getSingularType(type) {
            const singular = {
                workstreams: 'Workstream',
                projects: 'Project',
                commercial: 'Commercial Item'
            };
            return singular[type] || 'Item';
        }

        function getOrgName(org) {
            const names = {
                at: 'Auckland Transport',
                ac: 'Auckland Council',
                integrated: 'Integrated',
                commercial: 'Commercial',
                personal: 'Personal'
            };
            return names[org] || org;
        }

        function getOrgShortName(org) {
            const names = {
                at: 'AT',
                ac: 'AC',
                integrated: 'Integrated',
                commercial: 'Commercial',
                personal: 'Personal'
            };
            return names[org] || org;
        }

        function getPriorityIcon(priority) {
            const icons = {
                high: '🔴',
                medium: '🟡',
                low: '🟢'
            };
            return icons[priority] || '⚪';
        }

        function getFileIcon(filename) {
            const ext = filename.split('.').pop().toLowerCase();
            const icons = {
                pdf: '📄',
                doc: '📝',
                docx: '📝',
                xls: '📊',
                xlsx: '📊',
                ppt: '📊',
                pptx: '📊',
                jpg: '🖼️',
                jpeg: '🖼️',
                png: '🖼️',
                gif: '🖼️',
                html: '🌐',
                htm: '🌐',
                txt: '📄',
                default: '📎'
            };
            return icons[ext] || icons.default;
        }

        function getFileClass(filename) {
            const ext = filename.split('.').pop().toLowerCase();
            if (ext === 'pdf') return 'pdf';
            if (['html', 'htm'].includes(ext)) return 'html';
            return '';
        }

        function formatFileSize(bytes) {
            if (!bytes || bytes === 0) return '0 KB';
            const sizes = ['B', 'KB', 'MB', 'GB'];
            const i = Math.floor(Math.log(bytes) / Math.log(1024));
            return Math.round(bytes / Math.pow(1024, i) * 100) / 100 + ' ' + sizes[i];
        }

        function escapeHtml(text) {
            const div = document.createElement('div');
            div.textContent = text;
            return div.innerHTML;
        }

        function showNotification(message, type = 'success') {
            const notification = document.getElementById('notification');
            notification.textContent = message;
            notification.style.background = type === 'error' ? '#dc2626' : '#10b981';
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }

        function updateStats() {
            const totalItems = data.workstreams.length + 
                             data.projects.length + 
                             data.commercial.length;
            
            const activeWorkstreams = data.workstreams.filter(w => 
                w.priority === 'high' || w.priority === 'medium'
            ).length;
            
            const activeProjects = data.projects.filter(p => 
                p.priority === 'high' || p.priority === 'medium'
            ).length;
            
            let totalDocs = 0;
            ['workstreams', 'projects', 'commercial'].forEach(type => {
                data[type].forEach(item => {
                    if (item.files) totalDocs += item.files.length;
                });
            });
            totalDocs += data.vault.length;
            totalDocs += data.htmlDisplays.length;
            
            document.getElementById('totalItems').textContent = totalItems;
            document.getElementById('activeWorkstreams').textContent = activeWorkstreams;
            document.getElementById('activeProjects').textContent = activeProjects;
            document.getElementById('totalDocuments').textContent = totalDocs;
        }

        function updateVaultBadge() {
            document.getElementById('vaultBadge').textContent = data.vault.length;
        }

        // Data persistence
        function saveData() {
            try {
                // Create a clean copy of data to save
                const dataToSave = JSON.parse(JSON.stringify(data));
                
                // Ensure all items have proper structure
                ['workstreams', 'projects', 'commercial'].forEach(type => {
                    dataToSave[type].forEach(item => {
                        // Ensure files array exists
                        if (!item.files) item.files = [];
                        
                        // Ensure links array exists
                        if (!item.links) item.links = [];
                        
                        // Migrate old link field to links array if needed
                        if (item.link && item.links.length === 0) {
                            item.links.push({
                                id: generateId(),
                                name: item.link,
                                url: item.link
                            });
                        }
                    });
                });
                
                localStorage.setItem('myworkspace_data', JSON.stringify(dataToSave));
            } catch (e) {
                console.error('Failed to save data:', e);
                showNotification('Error saving data. Storage may be full.', 'error');
            }
        }

        function loadData() {
            try {
                const saved = localStorage.getItem('myworkspace_data');
                if (saved) {
                    const parsed = JSON.parse(saved);
                    
                    // Merge with default data structure
                    Object.keys(data).forEach(key => {
                        if (parsed[key] !== undefined) {
                            data[key] = parsed[key];
                        }
                    });
                    
                    // Ensure data integrity after load
                    ['workstreams', 'projects', 'commercial'].forEach(type => {
                        if (!Array.isArray(data[type])) data[type] = [];
                        
                        data[type].forEach(item => {
                            // Ensure required fields
                            if (!item.files) item.files = [];
                            if (!item.links) item.links = [];
                            if (!item.id) item.id = generateId();
                            if (!item.createdAt) item.createdAt = new Date().toISOString();
                            
                            // Migrate old link field if exists
                            if (item.link && item.links.length === 0) {
                                item.links.push({
                                    id: generateId(),
                                    name: item.link,
                                    url: item.link
                                });
                            }
                        });
                    });
                    
                    // Ensure vault array exists
                    if (!Array.isArray(data.vault)) data.vault = [];
                    
                    // Ensure categories array exists
                    if (!Array.isArray(data.categories)) {
                        data.categories = [
                            { id: 'cat-1', name: 'Project Documents', color: '#0066CC' },
                            { id: 'cat-2', name: 'Pacific Energy', color: '#FDCB6E' },
                            { id: 'cat-3', name: 'fixauckland Campaign', color: '#dc2626' }
                        ];
                    }
                    
                    // Ensure htmlDisplays array exists
                    if (!Array.isArray(data.htmlDisplays)) data.htmlDisplays = [];
                }
            } catch (e) {
                console.error('Failed to load data:', e);
                showNotification('Error loading saved data', 'error');
            }
        }

        // Initialize when DOM is ready
        document.addEventListener('DOMContentLoaded', init);
    </script>
</body>
</html>
